# Maltrail - malicious traffic detection system

<figure><img src="../../.gitbook/assets/68747470733a2f2f692e696d6775722e636f6d2f53643965716f612e706e67.png" alt=""><figcaption></figcaption></figure>

**Maltrail** is a malicious traffic detection system, utilizing publicly available (black)lists containing malicious and/or generally suspicious trails, along with static trails compiled from various AV reports and custom user defined lists, where trail can be anything from domain name (e.g. `zvpprsensinaix.com` for [Banjori](http://www.johannesbader.ch/2015/02/the-dga-of-banjori/) malware), URL (e.g. `hXXp://109.162.38.120/harsh02.exe` for known malicious [executable](https://www.virustotal.com/en/file/61f56f71b0b04b36d3ef0c14bbbc0df431290d93592d5dd6e3fffcc583ec1e12/analysis/)), IP address (e.g. `185.130.5.231` for known attacker) or HTTP User-Agent header value (e.g. `sqlmap` for automatic SQL injection and database takeover tool). Also, it uses (optional) advanced heuristic mechanisms that can help in discovery of unknown threats (e.g. new malware).

{% embed url="https://github.com/stamparm/maltrail/tree/master?tab=readme-ov-file" %}

### Docker

{% embed url="https://github.com/stamparm/maltrail/tree/master?tab=readme-ov-file" %}
