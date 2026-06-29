# Ollama

Ollama from my perspective is a framework that runs models/logic. It seems like docker to me, how docker is a framework and docker images are the models. The models are only ran when needed. So if you are talking to a model in chat that chat will be active in memory for like 5mins. After that it removes itself freeing up ram saving the conversation till needed again.

#### Install

1. Downloads and runs the Ollama installer. Sets it up as a background service that starts automatically on boot.

{% code overflow="wrap" %}
```
curl -fsSL https://ollama.com/install.sh | sh
```
{% endcode %}

2. Shows whether the Ollama service is active. You want to see `active (running)` in green.

{% code overflow="wrap" %}
```
systemctl status ollama
```
{% endcode %}

3. Downloads the model file (\~4.5GB) from Ollama's servers to your machine. Only need to do this once.

{% code overflow="wrap" %}
```
ollama pull qwen2.5:7b-instruct-q4_K_M
```
{% endcode %}

4. Opens a chat session right in your terminal to confirm the model works. Type `/bye` to exit.

{% code overflow="wrap" %}
```
ollama run qwen2.5:7b-instruct-q4_K_M
```
{% endcode %}

At this point if you see the chat in the terminal, this is the most basic sample of the AI. Can work for you if you want but i want a web UI 0\_o&#x20;

\--------------------------------------------------------------------------------— -----— -

5. Installs Python's package manager so you can install Open WebUI and agent frameworks. Skip if you already have it.
   1. if having a issue with pip3 try to install via pipx (same concept but run it in a environment)

{% code overflow="wrap" %}
```
sudo apt install python3-pip -y
```
{% endcode %}

6. Installs the web-based chat UI that sits on top of Ollama.

{% code overflow="wrap" %}
```
pip3 install open-webui
```
{% endcode %}

7. Starts the web UI. Keep this terminal open while you're using it.

{% code overflow="wrap" %}
```
open-webui serve
```
{% endcode %}

At this point you should be able to go to `localhost:8080` and see a web application with a chat window. This is how this model looks other models have different looking webpages or just the api visible this one has both.&#x20;

\-------— -    -   -------------------— -------------------— ----— --— ----------------— -

