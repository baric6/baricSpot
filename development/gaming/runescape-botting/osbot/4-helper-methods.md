# {4} helper methods

You have already seen the onLoop method in the Script class, but there are also other methods that you can optionally override:

The onStart method will be called when the script starts:

```
@Override
public final void onStart() {
    log("This will be printed to the logger when the script starts");
}
```

The onExit method will be called when the script exits

```
@Override
public final void onExit() {
    log("This will be printed to the logger when the script exits");
}
```

The onMessage method is called when a message arrives in the RuneScape chatbox:

```
@Override
public final void onMessage(final Message message) {
    log("A message arrived in the chatbox: " + message.getMessage());
}
```

The onPaint method provides you with a Graphics2D instance to draw on the screen:

```
@Override
public void onPaint(final Graphics2D g) {
    g.drawString("Some text", 10, 10);
}
```

The full list of methods in the Script class can be found here: http://osbot.org/api/org/osbot/rs07/script/Script.html
