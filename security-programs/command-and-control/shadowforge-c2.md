# ShadowForge C2

ShadowForge C2 is an API-centric Proof of Concept, similar to other C2s. The implant works with HTTP/v2 and TLS connecting over Zoom. The approach taken by this C2 is built upon an implementation strategy that leverages the capabilities of the Zoom Messaging Channel. The implant, residing within the compromised systems, establishes a connection to a designated Zoom Messaging Channel, serving as a secure and discreet communication medium. The domain used has a valid certificate, api.zoom.us.

{% embed url="https://github.com/0xEr3bus/ShadowForgeC2" %}
