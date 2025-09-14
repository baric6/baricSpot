# Cloning A detection ES8

1. find a detection you want to clone in our case it is "Excessive Failed Logins"
2. In the row of the detection you are wanting to clone all the way on the right there are 3 dots. Click them and hit clone
3. It will pop up a menu. Best practice add a unique name to tell the two detentions apart&#x20;
   1. \<your business> - Excessive Failed Logins
4. select enterprise security app if not already selected
5. under event-based detection
   1. The cloned app is set to guided we want manual
   2. under detection search
      1. we will be changing the default search. What we are wanting is the email to appear in the event alert&#x20;

```
| from datamodel:"Authentication"."Failed_Authentication"
| stats values("tag") as "tag", dc("user") as "user_count", values("user") as users, dc("dest") as "dest_count", count by "app","src"
| where 'count'>=3
```

6. Everything else can be default to keep it simple
7. save
8. turn alert on and wait for a event to happen
