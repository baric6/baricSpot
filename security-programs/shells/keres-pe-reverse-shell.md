# Keres PE reverse shell

Keres a is Powershell rev-shell backdoor with persistence

It generates a PE exe that spawns a powershell process that starts a powershell rev-shell with persistence (if process stops an other one is spawned , if process is running don t spawn new process)

Also it makes a batch and vbs file for persistent startup using reg.exe

You can add -Ps (optional) to generate only a .ps1 file

<figure><img src="../../.gitbook/assets/2023-12-31 09_49_35-Kali-Linux-2021.3-vmware-amd64 - VMware Workstation 17 Player (Non-commercial us.png" alt=""><figcaption></figcaption></figure>

Download

{% embed url="https://github.com/ELMERIKH/Keres" %}
