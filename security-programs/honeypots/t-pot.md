# T-Pot

<figure><img src="../../.gitbook/assets/image (456).png" alt=""><figcaption></figcaption></figure>

1. Get the latest ubuntu server (smaller) / desktop run it a VM I am using virtualbox (locally)
   1. Min requirements
      1. 8gb RAM
      2. 100gb HDD
      3. 2 cores
2. After you install the the VM
   1. `git clone https://github.com/telekom-security/tpotce`
   2. \
      `cd tpotce/iso/installer`<br>
   3. `sudo ./install.sh`
3. In the installer leave everything default&#x20;
   1. When i asks you about the type of honey pot
      1. **Hive <- everything, web UI**
      2. **Sensor <- no dashboard**
      3. **Mini <- no dashboard, limited logs**
      4. **Mobile <-** Not useful unless you’re testing cellular/IoT attacks
      5. **Tarpit <- no dashboard, logs**
   2. **Make a user and pass**
4. **It will install a lot may take a second**
5. **Web UI**
   1. `<ip>:64297` is the default for web&#x20;
6. connect to the server via ssh, on the live server the terminal don't scroll

#### Testing locally on a internal net

1. Use a VPN it worked for me&#x20;
2. NMAP&#x20;
   1. `nmap -Pn -vvv 172.12.63.128`
      1. Made up IP use your own&#x20;
3. Since you are internal you wont see anything in Attack map.
   1. Kibana <- Is were you will see data coming in

&#x20;
