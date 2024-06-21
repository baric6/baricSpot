# {12} Widgets

Widgets are individual elements of the RuneScape interface. They are represented in OSBot by the RS2Widget class. They are useful for when you need to interact with something on screen, but no API method exists allowing you to do that.

You can view the currently visible widgets at any time by enabling the Widgets setting in the Debug tab of the OSBot options:

When the widget setting is enabled, you can hover your mouse over different elements of the RuneScape GUI and see something like this:

Each different coloured box represents a different widget, and the corresponding widget ids can be seen in the same colour as the box on the left.

RS2Widgets are identified in a tree-like structure, an individual RS2Widget can have 1-3 ids.

Root id -> Second level id -> Third level id

In the example image above, the widget for the level tab icon has two ids: 548, 46.

548 is the root id, this means there is a parent widget with id 548, to which this widget belongs.

46 is the second level id, it identifies this widget in the children of parent widget 548.

Lets imagine the widget instead had the ids 548, 46, 3. That would mean that 548 is the root, 46 is the child of 548, and 3 is the child of 46 (this widget)

You can retrieve a widget in your script using the Widgets class, you can retrieve an instance of this class using the getWidgets() method in the MethodProvider class

For example, to retrieve the level tab icon widget:

```
RS2Widget levelTabIcon = getWidgets().get(548, 46);
```

Note that when retrieving a widget, if it does not exist on screen, the method will return null.

Some widgets may have text, for example, the "Join Chat" button in the clan chat tab:

Instead of using ids, we can retrieve this widget using it's text:

```
RS2Widget joinChatButton = getWidgets().getWidgetContainingText("Join Chat");
```

Like with the Entity class, the RS2Widget class implements the Interactable interface, meaning the RS2Widget class has an interact(String interaction) method, allowing us to interact with the widget.

Using the example of the "Join Chat" button again:

```
RS2Widget joinChatButton = getWidgets().getWidgetContainingText("Join Chat");
if (joinChatButton != null) {
    joinChatButton.interact("Join Chat"); 
}
```

### Hide contents

Configs are persistent id-value pairs that are updated on the RuneScape servers when certain events occur in game.

For example, there is a config for your player's attack style, it has a fixed id, and it's value changes whenever you select a different attack style in game.

There is also a config for your sound settings, and configs for quests, where the value indicates your player's progress through that quest.

Like with widgets, there is an option in the OSBot debug settings to enable a config view:

When you enable this you will see a list of id:value pairs appear:

If you then perform an action in game, for example changing attack style, you will see new id:value pairs appear at the top. If you have multiple id:value pairs with the same id, the highest one on the list displays the current value.

For example, the id of the config for attack style is 43.

When I start changing the attack style, I can see the config 43's value changing:

To retrieve a config's value, you can use the Configs class, to retrieve the instance of this class there is a getter method in the MethodProvider class

So to retrieve the current attack style I would write:

```
int attackStyle = getConfigs().get(43);
```

To check if the first attack style is selected I would write:

```
if (getConfigs().get(43) == 0) {
    // First attack style is selected
}
```
