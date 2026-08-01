---
description: >-
  You need to know how to connect computer over a network, if you are unsure
  they can talk "ping" is your best friend
---

# Connecting Local Ollama to a Local Splunk server using Python

#### The Setup

Splunk server:

* Refurbished old Desktop
* Ubuntu desktop
* 16gb DDR3
* i5
* Wired connection
* open ports 8089, 8000

Ollama server:

* Refurbished desktop hp
* Ubuntu Desktop
* 32gb DDR4
* i5
* Wired connection
* open port 11434

Both the Desktops at the higher end of processing i can see them struggling. For the task we are about to do is easy and can finish in about 2m to 5m depending on the model you are using, smaller models are not slower but tend to mess up more.

Ollama setup:

Model

* qwen3:30b-a3b (uses about 24g at the most, the 7b will work if you have 8-16gb ram)

Everything everything else is default - I tried to put Hermes AI and i was OK, it was slow (my hardware) and didn't quiet do what i was looking for. I wanted something that was a agent and could run programs for me, I hit a lot of blocks. I though maybe writing one would be easier ... 0\_o

I'm not going to lie I generated the boilerplate of the code to get a template, I have no idea what i am doing but learning along the way.&#x20;

What I got so far stumbling my way through it:

* All the Splunk documentation tells you to use a generated key, I have fought with that key and it got me nowhere
* Since this is local i am just using my admin user i setup with splunk, the docs will tell you to make a new user. The security guy in me wants to say, only do this if your network is not forward to the internet, Create a separate intranet. I digress i have a sandbox t0o play in :).
* Make sure to open ports or you are going to be spending 10m of work for a second task.

What i do is collect weather information and try to create predictions of bad weather. I live in tornado valley and i want a hint of a tornado is coming texted or emailed to me. Like the atmospheric pressure drops near me, also predicting black ice conditions for the morning drive.

{% code overflow="wrap" %}
```python
import requests, json, time, argparse, urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

# ── CONFIG ────────────────────────────────────────────────────────────────────
SPLUNK_HOST  = "https://<SPLUNK IP>:8089"
SPLUNK_USER  = "<SPLUNK USER>"
SPLUNK_PASS  = "SPLUNK PASS"
OLLAMA_HOST  = "http://<OLLAMA SERVER>:11434"
OLLAMA_MODEL = "qwen3:30b-a3b"
MAX_RESULTS  = 25
EARLIEST     = "-24h" # -6H, -2H
LATEST       = "now"
# ─────────────────────────────────────────────────────────────────────────────

SPLUNK_AUTH = (SPLUNK_USER, SPLUNK_PASS)
# THIS IS A LOT BUT IT IS BASIC INSTRUCTIONS, LIKE IT WILL READ THIS BEFORE PROCCESSING YOUR CHAT. IT JUST TELLS THE MODEL HOW TO THINK
SPL_SYSTEM = """\
You are a Splunk SPL expert. Convert the user's natural language question into a valid SPL query.
 
General rules:
- Return ONLY the raw SPL — no markdown, no backticks, no explanation
- Do NOT include a leading "search" keyword; the app adds that
- Use "head N" not "limit N" to limit results
- Never use foreach or rest commands for regular searches
- Always filter with where BEFORE table, never after
- In eval case() always use == for comparisons e.g. case(severity=="Extreme",3,severity=="Severe",2,1==1,0)
- Keep the SPL concise; avoid unnecessary fields or commands
- Use wildcards for partial matches e.g. | search event="*Tornado*" OR event="*Heat*"
- Use double quotes for string literals, single quotes for field names e.g. | eval 'my field'="value"
-
 
Weather index rules (index=weather):
- Always start with: index=weather sourcetype="weather:alerts" | spath
- Real field names after spath: area, certainty, description, effective, event, expires, headline, id, sender, sent, severity, status, urgency
- severity values: Extreme, Severe, Moderate, Minor, Unknown
- urgency values: Immediate, Expected, Future, Past, Unknown
- certainty values: Observed, Likely, Possible, Unlikely, Unknown
- area is a semicolon-separated string of county/region names e.g. "Dunn; Pepin; Chippewa; Eau Claire"
- To search by state use wildcard on area e.g. | search area="*califoria*" :>
- To search by event type e.g. | search event="*Tornado*" OR event="*Heat*"
- Skip expired alerts with: | where urgency!="Past"
- when searching for area, use wildcards e.g. | search "*califoria*" to match any county/region
- Never use wildcards (*) in where clauses — use "search" for wildcard filtering instead
- To filter by partial text: | search area="*califoria*" (use search, not where)
- Combine where and search: | where urgency!="Past" | search area="*califoria*"
- CRITICAL: wildcards (*) are NEVER allowed in where clauses. ALWAYS use | search field="*value*" for partial matches
"""
 # KEY POINTS OF ABOVE
SUMMARY_SYSTEM = """\
You are a weather and security analyst reviewing Splunk data.
Be concise. Highlight the most dangerous or urgent conditions first.
For weather: call out Extreme/Severe events, note affected areas, flag anything Immediate urgency.
If nothing notable, say so plainly.
"""


# ── Ollama ────────────────────────────────────────────────────────────────────

def ollama_chat(messages: list[dict]) -> str:
    r = requests.post(
        f"{OLLAMA_HOST}/api/chat",
        json={"model": OLLAMA_MODEL, "messages": messages, "stream": False},
        timeout=300,
    )
    r.raise_for_status()
    return r.json()["message"]["content"].strip()


def nl_to_spl(question: str, history: list[dict]) -> str:
    msgs = [{"role": "system", "content": SPL_SYSTEM}]
    msgs += history
    msgs.append({"role": "user", "content": question})
    return ollama_chat(msgs)


def summarize_results(question: str, spl: str, results: list[dict]) -> str:
    snippet = json.dumps(results[:15], indent=2)
    prompt = (
        f"Question: {question}\n"
        f"SPL used: {spl}\n"
        f"Result count: {len(results)}\n\n"
        f"Results (up to 15 shown):\n{snippet}"
    )
    return ollama_chat([
        {"role": "system", "content": SUMMARY_SYSTEM},
        {"role": "user", "content": prompt},
    ])

# ── Splunk ────────────────────────────────────────────────────────────────────

def run_spl(spl: str) -> list[dict]:
    search_str = spl if spl.lower().startswith("search ") else f"search {spl}"

    # create job
    r = requests.post(
        f"{SPLUNK_HOST}/services/search/jobs",
        auth=SPLUNK_AUTH,
        data={
            "search": search_str,
            "earliest_time": EARLIEST,
            "latest_time": LATEST,
            "output_mode": "json",
        },
        verify=False,
        timeout=30,
    )
    r.raise_for_status()
    sid = r.json()["sid"]

    # poll until done
    for _ in range(120):
        status_r = requests.get(
            f"{SPLUNK_HOST}/services/search/jobs/{sid}",
            auth=SPLUNK_AUTH,
            params={"output_mode": "json"},
            verify=False,
            timeout=10,
        )
        status_r.raise_for_status()
        content = status_r.json()["entry"][0]["content"]
        state = content["dispatchState"]
        if state == "DONE":
            break
        if state == "FAILED":
            raise RuntimeError(f"Splunk job failed: {content.get('messages', '')}")
        time.sleep(0.75)
    else:
        raise TimeoutError("Splunk job timed out")

    # fetch results
    results_r = requests.get(
        f"{SPLUNK_HOST}/services/search/jobs/{sid}/results",
        auth=SPLUNK_AUTH,
        params={"output_mode": "json", "count": MAX_RESULTS},
        verify=False,
        timeout=15,
    )
    results_r.raise_for_status()
    return results_r.json().get("results", [])

# ── CLI ───────────────────────────────────────────────────────────────────────

def fmt_results_table(results: list[dict]) -> str:
    if not results:
        return "  (no results)"
    priority = ["_time", "sourcetype", "host", "src_ip", "dest_ip", "user", "action", "status"]
    all_keys = list(results[0].keys())
    keys = [k for k in priority if k in all_keys]
    keys += [k for k in all_keys if k not in keys and not k.startswith("_")]
    keys = keys[:8]

    widths = {k: max(len(k), max(len(str(r.get(k, ""))) for r in results)) for k in keys}
    widths = {k: min(v, 40) for k, v in widths.items()}

    sep    = "  ".join("-" * widths[k] for k in keys)
    header = "  ".join(k.ljust(widths[k]) for k in keys)
    rows   = [header, sep]
    for r in results:
        rows.append("  ".join(str(r.get(k, "")).ljust(widths[k])[:widths[k]] for k in keys))
    return "\n".join(rows)


def chat(raw: bool = False, spl_only: bool = False):
    print(f"\n  Splunk+Ollama Chat")
    print(f"  model={OLLAMA_MODEL}  splunk={SPLUNK_HOST}  window={EARLIEST}")
    print("  Type a question. 'spl: <query>' to run raw SPL. 'quit' to exit.\n")

    history: list[dict] = []

    while True:
        try:
            q = input(">> ").strip()
        except (EOFError, KeyboardInterrupt):
            print()
            break
        if not q:
            continue
        if q.lower() in ("quit", "exit", "q"):
            break

        if q.lower().startswith("spl:"):
            spl = q[4:].strip()
            print(f"  SPL: {spl}")
        else:
            print("  [ollama] ...", end=" ", flush=True)
            try:
                spl = nl_to_spl(q, history)
            except Exception as e:
                print(f"\n  Ollama error: {e}")
                continue
            print(f"\n  SPL: {spl}")

        if spl_only:
            continue

        print("  [splunk] ...", end=" ", flush=True)
        try:
            results = run_spl(spl)
        except Exception as e:
            print(f"\n  Splunk error: {e}")
            continue
        print(f"{len(results)} result(s)\n")

        if not results:
            print("  No results.\n")
            history.append({"role": "user", "content": q})
            history.append({"role": "assistant", "content": spl})
            continue

        print(fmt_results_table(results))
        print()

        if raw:
            print(json.dumps(results, indent=2))
            print()
        else:
            print("  [ollama] summarizing...", end=" ", flush=True)
            try:
                summary = summarize_results(q, spl, results)
            except Exception as e:
                print(f"\n  Ollama error: {e}")
                continue
            print(f"\n{summary}\n")

        history.append({"role": "user", "content": q})
        history.append({"role": "assistant", "content": spl})
        if len(history) > 12:
            history = history[-12:]


if __name__ == "__main__":
    ap = argparse.ArgumentParser(description="Natural language Splunk search via Ollama")
    ap.add_argument("--raw",      action="store_true", help="Print raw JSON results")
    ap.add_argument("--spl-only", action="store_true", help="Generate SPL but don't run it")
    args = ap.parse_args()
    chat(raw=args.raw, spl_only=args.spl_only)
```
{% endcode %}

So lets break this down, you have three parts to this program

* Ollama&#x20;
* Splunk
* Cli

What runs first i the Cli part is what interact with both Splunk and Ollama. If the the Cli is working then you wont know what broken till you send a chat. There is a error built in to tell you what machine is having a problem.

If both are not connecting the Ollama error will fire first then Splunk. Say you got the Ollama error saying "could not connect".

* Make sure the port is open on Ollma server 11434
* Can you see the Splunk device on the network by pinging the ip address&#x20;
* Did you enable the service to run the Ollama API - 11434
