# (Windows) Agents and Deployment server

The agents are just a universal forwarder that can be setup manually or remotely for manual setup check out the splunk forwarder info on the side <<<<<

#### (Windows) How to setup the agent remotely and configure it&#x20;

1. Get the installer on the machine. Either by physically adding or use a software program that will push the executable to the machine&#x20;
2. Once the executable is on the machine you can run a power-shell script to install it and add the deployment to the machine &#x20;

```
msiexec.exe /i <Path to excutable>/splunkforwarder.msi DEPLOYMENT_SERVER="<Deployment Server>:8089" AGREETOLICENSE=Yes /quiet 
```

3. If you did this correctly yo should see the agents appear in the deployment server under&#x20;
4. Next we need to create a server class. A server class groups machines and pushes what apps the agents will be used (we will hit apps later)
   1. select the **"server classes tab",** then click the new server class button
      1. We will name the server class, in this case we will call it **"Window Machines"**
      2. This will take you to another page **containing a details, forwarders and application tabs** this is where we will add apps and forwarders to the class

