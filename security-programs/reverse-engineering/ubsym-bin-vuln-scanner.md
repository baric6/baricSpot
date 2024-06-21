# Ubsym Bin Vuln Scanner

UbSym attempts to improve the efficiency of symbolic execution technique and use it to detect a group of memory corruption vulnerabilities in binary programs. Instead of applying symbolic execution to the whole program, this tool initially determines a program test unit, probably containing vulnerability, using static analysis and based on the defined specifications for memory corruption vulnerabilities. Then the constraint tree of the program unit is extracted using symbolic execution so that every node in this constraint tree contains the desired path and vulnerability constraints. Finally, using the curve fitting technique and treatment learning the system inputs are estimated consistent with these constraints. Thus, new inputs are generated that reach the vulnerable instructions in the desired unit from the beginning of the program and cause vulnerability aactivation in those instructions.

<figure><img src="../../.gitbook/assets/CWE122_Heap_Based_Buffer_Overflow__c_CWE193_char_cpy_01_bad.png" alt=""><figcaption></figcaption></figure>

Download&#x20;

{% embed url="https://github.com/SoftwareSecurityLab/UbSym" %}
