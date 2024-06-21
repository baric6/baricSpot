# {8} Interactions

Now that you know how to retrieve the closest Entity to your player, you need to know how to interact with it.

Any class that implements the Interactable interface, will have an interact(String interaction) method.

The Entity class implements Interactable, therefore the Entity class has an interact(String interaction) method.

Here is a simple interaction example:

```
Entity tree = getObjects().closest("Tree");
if (tree != null) {
    tree.interact("Chop down");
}
```

In this example, we retrieve the closest Tree to the player, we check that the returned value is not null (because if no Tree exists, closest() will return null), and then perform the interaction "Chop down" on the tree.

This will result in the player clicking on the Tree, or right-clicking and selecting the "Chop down" option
