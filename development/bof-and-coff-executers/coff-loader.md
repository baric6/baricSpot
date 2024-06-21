# COFF Loader

This is a quick and dirty COFF loader (AKA Beacon Object Files). Currently can run un-modified BOF's so it can be used for testing without a CS agent running it. The only exception is that the injection related beacon compatibility functions are just empty.

The main goal is to provide a working example and maybe be useful to someone.

This is used to generate arguments for the COFFLoader code, if the BOF takes arguments simply add the arguments with the type expected with this and generate the hex string for use.

##

Download&#x20;

{% embed url="https://github.com/trustedsec/COFFLoader" %}
