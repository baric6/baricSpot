# BlueToolkit

BlueToolkit is an extensible Bluetooth Classic vulnerability testing framework that helps uncover new and old vulnerabilities in Bluetooth-enabled devices.

It works by executing templated exploits one by one and verifying appropriate properties based on the template logic. The toolkit is extensible and allows new research to be added to the centralized testing toolkit. There are 43 Bluetooth exploits available in the toolkit, from known public exploits and tools to custom-developed ones.

The framework works in a Black-box fashion, but it is also possible to operate the toolkit in a Gray-box fashion. For that one needs to extend the framework and connect it to the Operating System of the target so that it would be possible to observe Bluetooth logs and guarantee no false positives.

Also, we have already used our framework and were able to find [64 new vulnerabilities](https://github.com/sgxgsx/BlueToolkit#results) in 22 products.

We have a [dedicated repository](https://github.com/sgxgsx) that provides various types of vulnerability templates.

{% embed url="https://github.com/sgxgsx/BlueToolkit" %}
