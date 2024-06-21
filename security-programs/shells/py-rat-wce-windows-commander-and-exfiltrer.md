# (py rat) WCE Windows Commander and Exfiltrer

&#x20;

{% embed url="https://user-images.githubusercontent.com/66295316/227532825-039ba192-10b6-4688-bc9f-3c10fc7c8701.png" %}

The WCE is a Python-based tool that allows sending commands to a compromised network node through IP packet window flags using TCP, with calculated checksum and other metrics that make the packet look legitimate and hard to detect. The tool implements ROT13 to obfuscate the commands, making it more difficult for defenders to identify them.

The tool consists of two scripts: the commander and the receiver. The commander script runs on the attacker's machine and sends commands to the victim's machine. The receiver script runs on the victim's machine, listening for packets on a specific port. The victim machine should have access to a socket and a network interface to monitor the packet.

The commander script takes several parameters, such as the source and destination IP and port, delay between each packet, and the command to be sent. The receiver script listens on a specific port and executes the received commands.

One of the unique features of WCE is that there is no need for the attacker to send the packet to the victim directly. Instead, having the malicious packet flowing in the network is enough. The receiver script will take the window packets from specific ports and with a specific count and then execute them. This makes the tool more versatile and easier to use in various network environments.

The WCE tool is designed to make exfiltration and network command more stealthy by using window flags, which are often overlooked by security monitoring tools. By implementing a reliable and customizable transmission method using TCP, it helps attackers evade detection and exfiltrate sensitive data.

Download&#x20;

{% embed url="https://github.com/Cyber-Guy1/WCE" %}
