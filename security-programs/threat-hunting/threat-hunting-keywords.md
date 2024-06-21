# Threat Hunting keywords

<figure><img src="../../.gitbook/assets/thk2.png" alt=""><figcaption></figcaption></figure>

This List can be valuable for ThreatHunters, SOC and CERT teams for static analysis on SIEM as it assists in identifying threat actors (or redteamers 😆) using default configurations from renowned exploitation tools in logs. It differs from IOC feeds in its enduring relevance: the keywords here have no 'expiration dates' and can detect threats years after their inclusion, they are flexible accepting wildcard and non sensitive case matches and only focused on default keywords.

Primarily designed for Threat Hunting, this list can be useful in complex scenarios. Whether you have access to a SIEM you don't manage, with unparsed data, or if you're part of a SOC team with a well-managed SIEM, the examples provided here can expedite the process of detecting malicious activity without the necessity to parse anything. If your logs are already parsed, this list can be used to match fields within your data, potentially transforming into a detection rule based on the keyword type category you select, provided the false positive rate is sufficiently low.

Download

{% embed url="https://github.com/mthcht/ThreatHunting-Keywords" %}
