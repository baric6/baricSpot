# {10} Items and ItemContainers (Inventory, Bank, Equipment, Store, ...)

Items such as "Logs" and "Bones" are represented by the Item class

The Item class provides various different useful methods such as getName() to return the name of an item, getAmount() to return the amount of the item (e.g. the amount of the item in your inventory, or the amount of the item in the bank), isNote() and getActions() which returns a String\[] of all the possible actions your player could perform on the item.

Like with the Entity class, the Item class implements the Interactable interface, which provides you with an interact(String interaction) method.

So in the same way as you would interact with a Tree Entity to chop it down, you can interact with an Item, for example to eat it.

Items are stored inside of ItemContainers, and so to retrieve an instance of Item you must retrieve it from the relevant ItemContainer.

The current available ItemContainers are: Bank, DepositBox, Equipment, Inventory, Store, Trade.OurOffer, Trade.TheirOffer

You can retrieve the instances of these ItemContainers using the associated getter methods in the MethodProvider class:

```
getInventory(); // returns the instance of Inventory
getBank(); // returns the instance of Bank (or null if the player is not near a bank)
getEquipment(); // returns the instance of Equipment
```

Note that, getBank() and getDepositBox() will both return null if your player is not close to a bank or deposit box, and so you must check that the returned instance is not null before calling any methods on it.

All of the ItemContainers share the same useful methods:

```
boolean contains(...) // Check if the ItemContainer contains any items with the specified names, ids, filters etc.
long getAmount(...) // Get the sum of the amount of items matching the specified name, ids, filters etc.
Item getItem(...) // Get the Item with matching name, id etc. or null if it does not exist
```

But each of the classes that extend ItemContainer will have some extra methods added to them. For example, the Bank class also defines the methods:

```
boolean isOpen(); // Check if the Bank is open
boolean open(); // Open the bank
boolean withdraw(...) // Withdraw an item from the bank
```

Both the Bank and DepositBox require you to open them before you can use any of the methods.

Here is an example of using an ItemContainer, getting a Lobster item from the Inventory and eating it:

```
if (getInventory().contains("Lobster")) {
    if (getInventory().getSelectedItemName() == null) {
        getInventory().getItem("Lobster").interact("Eat"); 
    } else {
        getInventory().deselectItem(); 
    }
}
```
