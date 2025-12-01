# Silver C2

Sliver is an open source cross-platform adversary emulation/red team framework, it can be used by organizations of all sizes to perform security testing. Sliver's implants support C2 over Mutual TLS (mTLS), WireGuard, HTTP(S), and DNS and are dynamically compiled with per-binary asymmetric encryption keys.

The server and client support MacOS, Windows, and Linux. Implants are supported on MacOS, Windows, and Linux (and possibly every Golang compiler target but we've not tested them all).

{% embed url="https://github.com/BishopFox/sliver" %}

#### Note

* Silver has to have a agent on exploited machine then it can run bof / coff files to collect data and send back to the C2
* Silver has a lot roles that can be done with the agent
  * ransomware&#x20;
  * monitoring users &#x20;
  * file upload and download
  * remote execution&#x20;

