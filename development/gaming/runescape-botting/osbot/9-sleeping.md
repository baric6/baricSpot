# {9} Sleeping

n the previous section I showed you how to interact with the closest Tree to the player. However, if you tried that you would notice that the bot spam clicks on the Tree. This is where sleeping comes in.

There are three main ways to sleep in a script:

```
Returning an integer value from the onLoop() method, this will result in the ScriptExecutor sleeping for the specified number of ms
Calling the sleep(long ms) method in the MethodProvider class, note this method is static and so you can write: MethodProvider.sleep(long ms)
Using a ConditionalSleep (sleep until a condition is matched, or until a specified timeout is reached)
```

Wherever possible I would recommend that you use ConditionalSleeps. You can use a ConditionalSleep like so:

```
Entity tree = getObjects().closest("Tree");
if (tree != null && tree.interact("Chop down")) {
      new ConditionalSleep(5000) {
        @Override
        public boolean condition() {
            return myPlayer().isAnimating() || !tree.exists();
        }
    }.sleep();
}
```

What this snippet does is:

```
Get the closest Tree to the player
Check the tree value is not null (because if it is null, no tree exists and so we don't wan't to do anything)
Perform the "Chop down" interaction on the tree
Check that the interact() method returned true, if the return value is false, the interaction failed and we do not want to sleep
Create a new ConditionalSleep with timeout set to 5000ms (5 seconds)
Override the ConditionalSleep's condition so that we stop sleeping before the timeout if either the player is animating (chopping the tree), or the tree no longer exists (someone else has chopped it down)
Call the ConditionalSleep's sleep() method to start sleeping.
```

As you will be using the CondtionalSleep class frequently, you may want to use an alternative that I wrote, just so that your script is less cluttered:

```
package util;

import org.osbot.rs07.utility.ConditionalSleep;

import java.util.function.BooleanSupplier;

public final class Sleep extends ConditionalSleep {

    private final BooleanSupplier condition;

    public Sleep(final BooleanSupplier condition, final int timeout) {
        super(timeout);
        this.condition = condition;
    }

    @Override
    public final boolean condition() throws InterruptedException {
        return condition.getAsBoolean();
    }

    public static boolean sleepUntil(final BooleanSupplier condition, final int timeout) {
        return new Sleep(condition, timeout).sleep();
    }
}
```

Using this class, you do not have to override the condition() method, instead you can pass a BooleanSupplier as the condition. Here is the same snippet as before, but using this Sleep class instead:

```
Entity tree = getObjects().closest("Tree");
if (tree != null && tree.interact("Chop down")) {
    Sleep.sleepUntil(() -> myPlayer().isAnimating() || !tree.exists(), 5000);
}
```

Or:

```
Entity tree = getObjects().closest("Tree");
if (tree != null && tree.interact("Chop down")) {
    new Sleep(() -> myPlayer().isAnimating() || !tree.exists(), 5000).sleep();
}
```

Some methods in the OSBot API will already have sleeps built into them, and so you do not need to add your own, for example the method getTabs().open(Tab.INVENTORY) will sleep until the inventory tab is open.
