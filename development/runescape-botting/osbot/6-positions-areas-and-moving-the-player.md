# {6} Positions, areas and moving the player

The RuneScape world is split into tiles, each tile has an (x, y, z) coordinate associated with it:

```
x coordinate increases as you move East across the world, and decreases as you move West.

y coordinate increases as you move North, decreases as you move South

z coordinate increases as you move "up" e.g. climbing up a staircase, and decreases as you go "down" e.g. climbing down a staircase.
```

To get the (x, y, z) coordinate of a tile, or create a path or area you have a few options:

```
Use the Entity hover debugger by hovering over a tile, this is enabled in the settings of the OSBot client.
Using an OSBot script such as https://osbot.org/forum/topic/84109-explvs-location-assistant-free-paths-areas/ 
Or using a map tool that I created: https://explv.github.io/
```

In the OSBot API (x, y, z) coordinates are represented with the Position class.

You can create a new Position like so:

```
Position position = new Position(x, y, z);
```

You can retrieve the Position of the Player by calling the myPosition() method in the MethodProvider class:

```
Position position = myPosition();
```

All Entities such as NPCs, Players, RS2Objects, GroundItems have a method to get their position called getPosition():

```
Entity bones = getGroundItems().closest("Bones");
if (bones != null) {
    Position bonesPosition = bones.getPosition();
}
```

An Area is a polygon consisting of one or more Positions.

You can create an Area in a few different ways:

```
Area area = new Area(int[][] positions); // Constructs a polygonal area using each set in a 2d array as a pair of x and y position coordinates.
Area area = new Area(int x1, int y1, int x2, int y2); // Constructs a rectangular area using x and y coordinates from two separate positions.
Area area = new Area(Position[] positions); // Constructs a polygonal area using each position as a point in the polygon.
Area area = new Area(Position southWest, Position northEast); // Constructs a rectangular area using two positions 
```

Areas are typically used to determine if an entity is in a certain location in the RuneScape world or for walking to a certain location.

For example, to determine if your player is in the Varrock West bank you would write:

```
if (Banks.VARROCK_WEST.contains(myPosition())) { // VARROCK_WEST is a static Area variable found in the Banks class
    // The player is in the Varrock West bank
}
```

To move your player to an Area or Position, you can use the Walking class. To access the Walking instance you use the getWaking() method in the MethodProvider class.

There are three main methods of walking in the Walking class, either walking to a nearby position with the same z coordinate as the player's position using the walk method, note that the destination must be close to your Player otherwise it will not be able to find a path:

```
getWalking().walk(new Position(x, y, z)); // Walks to the Position with coordinates x, y, z

getWalking().walk(new Area(x1, y1, x2, y2)); // Walks to a Position in the Area with coordinates x1, y1, x2, y2

getWalking().walk(entity); // Walks to the entity's position.
```

Walking along a fixed path (all positions must have the same z coordinate as the player's current position):

```
List<Position> path = new ArrayList<>();
path.add(new Position(x, y, z));
path.add(new Position(x, y, z));
// etc.
  
getWalking().walkPath(path);
```

Or for long distances, where the destination tile is not visible to the player, and creating a fixed path would be inappropriate, you can use web walking:

```
getWalking().webWalk(Banks.VARROCK_WEST); // Will attempt to walk to the Varrock West bank from anywhere in the RuneScape world
```

When using web walking, common obstacles such as staircases and gates will be handled for you, which also means you can web walk to positions with different z coordinates to the player's current position.

Due to the nature of web walking, in some less commonly traveled locations in the RuneScape world, the web walker may not be able to find a path to your destination, when this occurs, you can use a different walking method to a location where you can web walk from, and also request that web walking links be added: https://osbot.org/forum/forum/335-web-walking-links/
