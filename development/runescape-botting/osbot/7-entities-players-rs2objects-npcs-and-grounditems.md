# {7} Entities (Players, RS2Objects, NPCs and GroundItems)

Players, RS2Objects, NPCs and GroundItems are the main entities that you will be using in your scripts.

To access these, again, there are getter methods in the MethodProvider class:

```
getPlayers() // returns an instance of Players
getNpcs() // returns an instance of NPCS
getGroundItems() // returns an instance of GroundItems
getObjects() // returns an instance of Objects
```

The Players class is used for retrieving the Player instances near your character.

The NPCS class is used for retrieving NPCS, for example Cows in Lumbridge

The GroundItems class is used for retrieving GroundItems, for example bones on the ground

The Objects class is used for retrieving RS2Objects, for example Trees

Each of these classes extend the EntityAPI class. The EntityAPI provides methods such as closest() for getting the closest Entity to your player, get(x, y) to get the Entity at the specified x, y coordinates on the same plane as your player, and iterator() to return an Iterator of the collection of entities near your player.

An example of using one of the closest() methods is:

```
Entity cow = getNpcs().closest("Cow");
```

This will return the closest Cow to your player, or null if no Cow exists.
