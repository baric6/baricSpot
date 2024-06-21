# {5} accessing the Inventory, Bank, Player, etc. instances

The Script class as you have already seen, extends a class called MethodProvider.

The MethodProvider class contains many useful variables, and getter methods for those variables, this is how you access the core parts of the OSBot API.

Because the Script class extends MethodProvider, and your main class extends the Script class, you can also access these variables and getter methods from within your main script class:

```
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

@ScriptManifest(author = "Explv", name = "An Example Script", info = "", version = 0.1, logo = "")
public final class ExampleScript extends Script  {
    
    @Override
    public final int onLoop() throws InterruptedException {
        getInventory(); // returns the Inventory instance
        myPlayer(); // returns the Player instance
        getWalking(); // returns the Walking instance
        return 0;
    }
}
```

This also means that if you want to access these methods from other classes, you must pass your instance of MethodProvider to instances of those other classes:

```
import org.osbot.rs07.script.MethodProvider;
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

@ScriptManifest(author = "Explv", name = "An Example Script", info = "", version = 0.1, logo = "")
public final class ExampleScript extends Script  {
    @Override
    public final int onLoop() throws InterruptedException {
        SomeOtherClass someOtherClass = new SomeOtherClass(this);
        return 0;
    }
}

final class SomeOtherClass {
    private final MethodProvider methods;

    public SomeOtherClass(final MethodProvider methods) {
        this.methods = methods;
    }
  
    public final void someMethod() {
        methods.getInventory(); // I can now access the Inventory instance from this class 
    }
}
```
