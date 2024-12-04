# Native Bypass CredGuard

Need to compile C# or C++ to a executable&#x20;

NativeBypassCredGuard is a tool designed to bypass Credential Guard by patching WDigest.dll using only NTAPI functions (exported by ntdll.dll). It is available in two flavours: C# and C++.

The tool locates the pattern "39 ?? ?? ?? ?? 00 8b ?? ?? ?? ?? 00" in the WDigest.dll file on disk (as explained in the first post in the Refences section, the pattern is present in this file in all Windows versions), then calculates the necessary memory addresses, and finally patches the value of two variables within WDigest.dll: _g\_fParameter\_UseLogonCredential_ (to 1) and _g\_IsCredGuardEnabled_ (to 0).

This forces plaintext credential storage in memory, ensuring that from that point forward credentials are stored in cleartext whenever users log in. As a result, next time the LSASS process is dumped it may contain passwords in plaintext.

{% embed url="https://github.com/ricardojoserf/NativeBypassCredGuard" %}
