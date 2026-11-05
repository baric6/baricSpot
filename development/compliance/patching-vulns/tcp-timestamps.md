# TCP timestamps

&#x20;This finding means the host leaks an approximate uptime, which hints at its patch level. It has no other impact.

**Windows:** `netsh int tcp set global timestamps=disabled`

\*\*Warning\*\*

Disabling timestamps can slightly hurt performance on high-bandwidth or high-latency links. Most organizations accept this finding on internal hosts.

