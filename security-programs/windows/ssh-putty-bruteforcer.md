# SSH Putty bruteforcer

The ssh-putty-brute.ps1 is a wrapper script which uses PuTTY clients (either putty.exe or plink.exe) to perform SSH login bruteforce attacks.

import-module .\ssh-putty-brute.ps1

## Usage:

ssh-putty-brute \[-h ip|ips.txt] \[-p port] \[-u user|users.txt] \[-pw pass|pwdlist.txt]

## Examples:

ssh-putty-brute -h 10.10.5.11 -p 22 -u root -pw P@ssw0rd ssh-putty-brute -h 10.10.5.11 -p 22 -u root -pw (Get-Content .\pwdlist.txt)

Download

{% embed url="https://github.com/InfosecMatter/SSH-PuTTY-login-bruteforcer" %}
