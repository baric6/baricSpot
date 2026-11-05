# TCP timestamps

This finding means the host leaks an approximate uptime, which hints at its patch level. It has no other impact.

**Windows:** `netsh int tcp set global timestamps=disabled`

