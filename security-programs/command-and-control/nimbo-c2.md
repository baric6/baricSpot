# Nimbo-C2

Nimbo-C2 agent supports x64 Windows & Linux. It's written in Nim, with some usage of .NET on Windows (by dynamically loading the CLR to the process). Nim is powerful, but interacting with Windows is much easier and robust using Powershell, hence this combination is made. The Linux agent is slimer and capable only of basic commands, including ELF loading using the memfd technique.

{% embed url="https://github.com/itaymigdal/Nimbo-C2" %}
