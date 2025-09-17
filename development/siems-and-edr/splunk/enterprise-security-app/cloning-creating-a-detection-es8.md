# Cloning/Creating A detection ES8

1. Find a detection you want to clone in our case it is "Excessive Failed Logins"
2. In the row of the detection you are wanting to clone all the way on the right there are 3 dots. Click them and hit clone
3. It will pop up a menu. Best practice add a unique name to tell the two detentions apart&#x20;
   1. \<your business> - Excessive Failed Logins
4. Select enterprise security app if not already selected
5. Under event-based detection
   1. The cloned app is set to guided we want manual
   2. Under detection search
      1. We will be changing the default search. What we are wanting is the email to appear in the event alert&#x20;

```
| from datamodel:"Authentication"."Failed_Authentication"
| bin _time span=5m
| stats values(tag) as tag,
        dc(user) as user_count,
        values(user) as users,
        dc(dest) as dest_count,
        count by app, src, _time
| where count >= 6
| iplocation src
| table _time app src Country users user_count dest_count count
```

5.1. _(Side note)Having a table as the out seem to work best for me._&#x20;

_Example_

```
| table _time app src Country users user_count dest_count count
```

6. In the Analyst Queue
   1. Title **(since the output of the main search is in a table you can use the vars in anything below the first search box)**
      1. $users$ Excessive Failed Logins -> baric@123fake.xyz Excessive Failed login
   2. Description **(The same var rules apply here as above)**&#x20;
   3. Drill down Searches **(Sub Searches that take in vars from the main search to dig deeper, must be clicked does not auto populate)**
      1. **Name (can also use the vars from the main search )**
         1. Search for $src$

Below is a example, on what you can put&#x20;

```
index=* src="$src$"
| table _time user src app action dest _raw
| sort -_time
```

7. Throttling
   1. I have mirrored the default detection's to have it run every 23 hours&#x20;
      1. I have found that some searches will run every time when you set a time and will fill up the analyst Queue
      2. Setting it to 86300 seconds witch is roughly 23 hours it works better ....
