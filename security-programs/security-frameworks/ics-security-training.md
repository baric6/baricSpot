# ICS Security training

&#x20;The simulation VM (named ChemicalPlant) runs a realistic simulation of a chemical process reaction that is controlled and monitored by simulated remote IO devices through a simple JSON API. These remote IO devices are then monitored and controlled by the PLC VM using the Modbus protocol. This VM is located in the ICS network subnet (192.168.95.0/24) with the IP addresses 192.168.95.10-192.168.95.15

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

## Programmable Logic Controller

The PLC VM (named plc\_2) is a modified version of OpenPLC (https://github.com/thiagoralves/OpenPLC\_v2) that uses an older version of the libmodbus library with known buffer overflow vulnerabilities. This VM is located in the ICS network subnet (192.168.95.0/24) at 192.168.95.2

Download

{% embed url="https://github.com/Fortiphyd/GRFICSv2" %}
