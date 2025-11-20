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
         1. **Details** - configuration about the class (as long as it is working keep default)
         2. **Forwarders** - where you will assign the endpoints to the class
         3. **Application** - where you assign the applications you put in the development-apps folders&#x20;
         4. this is made we will come back here later&#x20;
5. Creating a application or adding one through Splunkbase
   1. Custom apps or splunkbase apps go into `<splunkhome>\etc\deployment-apps`.&#x20;
   2. Creating a app
      1. Under the deployment apps folder create a folder named \<Your app> this can be called anything
      2. Under \<Your app> make two files — **Make sure you save these files from notepad as a .conf. If you create the file using right click it will append file.conf.txt and this will not work. I spent hours debugging this. To check in file explorer navigate to your folder and click view > view hidden file extension.**
         1. **inputs.conf** — this is what data you are going to push to Splunk from the endpoint — below is getting basic event logs &#x20;
            1.  **`[WinEventLog://Security]`**\
                **`checkpointInterval = 5`**\
                **`current_only = 0`**\
                **`disabled = 0`**\
                **`start_from = oldest`**

                `[WinEventLog://Application]`\
                `checkpointInterval = 5`\
                `current_only = 0`\
                `disabled = 0`\
                `start_from = oldest`

                **`[WinEventLog://System]`**\
                **`checkpointInterval = 5`**\
                **`current_only = 0`**\
                **`disabled = 0`**\
                **`start_from = oldest`**
         2. **outputs.conf** — this file connects your agent on the endpoint
            1.  `[tcpout]`\
                `defaultGroup = default-autolb-group`

                `[tcpout:default-autolb-group]`\
                `server = gesmv-hq-lpsfty:9997`
         3. After these are made the deployment server should be able to see it
   3. OR Adding A Splunkbase app
      1. &#x20;Any agent can use this app it is a basic viewer for the conf of a agent
         1. [https://splunkbase.splunk.com/app/7796](https://splunkbase.splunk.com/app/7796)
      2. extract the zip and place the extracted folder  `<splunkhome>\etc\deployment-apps`
      3. once the folder is in there you should see it pop up in the deployment server apps
   4. Once you have added these you are done head back to the Agent Management UI in Splunk
6. Adding forwarders to the server class
   1. Going back to the **server class page**, you will see a button in the upper right hand side saying edit forwarders, click it
   2. when  you are on the forwarders page you will see three boxes **Include, filter by machine type and exclude.** This is the way you will add the machines to the server class
      1. **Include** - search by client name, host name, IP address, or DNS name. Examples: 185.2.3._, fwdr-_
      2. **Filter by machine** - search by type of machine linux or windows or if you have any other device types
      3. **Exclude** - pick all but selected devices search by client name, host name, IP address, or DNS name. Examples: 185.2.3._, fwdr-_
   3. We will search by include for now and by device name we have devices named "Windows" and "Linux" for example. We will type in "Windows" and hit the preview button, there should be a check mark next to the Windows machine and not next to the Linux machine. This means we will apply the server class to only the Windows machine.&#x20;
      1. **Note** — **if you are adding server classes to new machines and you already have machines with the server class. You have to select the old machines with the new ones or you will remove the server class from the old and only apply it to the machines selected.** **(have not found a way around this and annoying when you have a lot of machines)**
   4. After you are happy with what machines you will apply this to (check marks on the correct machine(s)). Click the save button.
   5. It will take you back to the server class page under the forwarders tab and you should now see your devices with a pending hourglass. Setting the server class will take up to five mins to see the effects. Refreshing the you should see the hourglass change to a check mark and that means the server class with the apps have been added to the forwarder.
   6. check the search to see your data start flowing

