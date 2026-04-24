# (Windows) Running Python in task scheduler

#### Before setting a script to run with Task Scheduler make sure you python script works by itself. The only think Task Scheduler is doing is running you code at certain times. Your code has to work first

**Using Task Scheduler and python you don't need to put the program in a loop. If it runs once then you can put it in a schedule to run .**

#### Location of script

How to make a script a process in task scheduler:

1. Find the location of you python install file on windows using power shell

```
Get-Command python
```

* Output should look like

```
C:\Users\<your user>\AppData\Local\Programs\Python\Python314\python.exe
```

2. Get full path to you script
   1. Find you main python file&#x20;
      1. &#x20;Right click >  properties > location (this is just the folder so you have to append you file name)
   2. **NOTE** -  You can point it to a folder that say it reads a file of IP or outputs a file of IP it still should work&#x20;

```
C:\Users\<your user>\Desktop\IPlookupV2\IPlookup\ipLookup.py
```

3. From above just grab the file location without the file name&#x20;

```
C:\Users\<your user>\Desktop\IPlookupV2\IPlookup\
```

#### Creating the task&#x20;

1. Open task scheduler
2. &#x20;Click create task (not basic task, you will have more control)
3. **general**
   1. Name it whatever
   2. &#x20;Security options select
      1. Run whether user is logged in or not&#x20;
      2. Run with highest privileges (if admin)
4. **triggers > new**
   1. Begin the task : On a schedule
   2. &#x20;Daily > Recur every 1 days
   3. Repeat task ever 6 hours for a duration of indefinitely
      1. If the drop down don't have your hour just write it in the box&#x20;
   4. Check enabled &#x20;

<figure><img src="../../../../.gitbook/assets/image (468).png" alt=""><figcaption></figcaption></figure>

5. **Action > New**
   1. Action: Start a program&#x20;
   2. Program / Script
      1. Path to python executable&#x20;
   3. Add argument
      1. Path to you python script
   4. Start in&#x20;
      1. Path to the folder you python script lives in&#x20;

<figure><img src="../../../../.gitbook/assets/image (469).png" alt=""><figcaption></figcaption></figure>

6. Hit on and save the task it should run as soon as you save it if under trigger the Start section is default&#x20;
   1. If not find it in you task scheduler
      1. Right click > run &#x20;
