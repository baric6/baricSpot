# {11} Filtering

In the previous sections I showed you how to retrieve the closest Entity to the player using it's name, and also how to retrieve an Item using its name from an ItemContainer.

There will be cases however where using just the name of the Identifiable is not enough, and you want to retrieve an Item or Entity based on more conditions, this is where filtering comes in.

As I mentioned previously, the Players, GroundItems, NPCS and Objects classes all extend the EntityAPI class which provides the closest() method and a few others.

One of the "closest" methods the EntityAPI provides is:

```
E closest(Filter<E>... filters)
```

What this method allows you to do is retrieve the closest Entity to the player, that matches the Filters that you provide.

The Filter interface is very simple, it contains only a single method:

```
boolean match(V obj);
```

When you create a new Filter, because it is an interface, you must provide an implementation for this method. The implementation should return true if the object matches your criteria, and false if it does not.

For example, if we want to create a Filter that only returns true if the Entity's name begins with "Cow", we would write:

```
Filter<Entity> cowFilter = new Filter<>() {
    @Override
    public boolean match(final Entity entity) {
        return entity.getName().startsWith("Cow");
    }
};
```

We can then use this Filter as a parameter to the EntityAPI's closest(Filter filter) method, to retrieve the closest Entity who's name begins with "Cow":

```
Entity cow = getNpcs().closest(cowFilter);
```

In the OSBot API, you will find several predefined Filters that you can make use of: ActionFilter, AreaFilter, ContainsModelFilter, ContainsNameFilter, IdFilter, ItemListFilter, ModelFilter, NameFilter, PositionFilter

The EntityAPI class, which Players, Objects etc. extend, extends the FilterAPI class

The FilterAPI class provides you with more filtering methods:

```
java.util.List<E> filter(java.util.Collection<E> entities, Filter<E>... filters)
java.util.List<E> filter(Filter<E>... filters)
E singleFilter(java.util.Collection<E> entities, Filter<E>... filters)
```

The filter() methods will apply your Filters to a collection of objects, returning a List of the ones that matched.

The singleFilter() method will apply your Filters to a collection of objects, and return a single object that matched (there may be more than one that matched, but the method will return just one).

So for example, instead of using closest(cowFilter) to return the closest Cow to the player, you could write:

```
Entity cow = getNpcs().singleFilter(getNpcs().getAll(), cowFilter);
```

Which would return a Cow near to your player (or null if no cow exists), but not necessarily the closest Cow.

You can also use Filters for some methods in the ItemContainer class, for example, to check if the Inventory contains a pickaxe you might write:

```
Filter<Item> pickaxeFilter = new Filter<>() {
    @Override
    public boolean match(final Item item) {
        return item.getName().endsWith("pickaxe"); 
    }
}

if (getInventory().contains(pickaxeFilter)) {
    // inventory contains a pickaxe 
}

```

Because the Filter interface is a FunctionalInterface we can use lambda expressions to declare the Filter, which looks cleaner and saves some typing. Using a lambda expression we can write the snippet above as:

```
if (getInventory().contains(item -> item.getName().endsWith("pickaxe")) {
    // inventory contains a pickaxe 
}
```

This simply means, if the inventory contains an item where the item's name ends with "pickaxe", return true, otherwise return false.
