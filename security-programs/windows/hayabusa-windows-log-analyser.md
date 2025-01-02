# Hayabusa windows log analyser

<figure><img src="../../.gitbook/assets/image (288).png" alt=""><figcaption></figcaption></figure>

Hayabusa is a Windows event log fast forensics timeline generator and threat hunting tool created by the Yamato Security group in Japan. Hayabusa means "peregrine falcon" in Japanese and was chosen as peregrine falcons are the fastest animal in the world, great at hunting and highly trainable. It is written in Rust and supports multi-threading in order to be as fast as possible. We have provided a tool to convert Sigma rules into Hayabusa rule format. The Sigma-compatible Hayabusa detection rules are written in YML in order to be as easily customizable and extensible as possible. Hayabusa can be run either on single running systems for live analysis, by gathering logs from single or multiple systems for offline analysis, or by running the Hayabusa artifact with Velociraptor for enterprise-wide threat hunting and incident response. The output will be consolidated into a single CSV timeline for easy analysis in Excel, Timeline Explorer, Elastic Stack, Timesketch, etc...&#x20;

Download&#x20;

{% embed url="https://github.com/Yamato-Security/hayabusa" %}
