# {2} basic script

1. Add a new class to your project (by right clicking on the src/ directory and select New -> Java Class)
2. Give the class an appropriate name, this class will be the entry point to your script, so a name such as Woodcutter for a woodcutting script would make sense.
3. Add the following code:

```
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

@ScriptManifest(author = "Explv", name = "An Example Script", info = "Just an empty script :(", version = 0.1, logo = "")
public final class ExampleScript extends Script  {
    @Override
    public final int onLoop() throws InterruptedException {
        return 0;
    }
}
```

This is the ScriptManifest annotation:

```
@ScriptManifest(author = "Explv", name = "An Example Script", info = "Just an empty script :(", version = 0.1, logo = "")
```

It is required that your main class has this annotation, as it provides information used in the OSBot script selector. Set author to your OSBot username, name to the name of your script, info to a short description etc.

For the logo parameter, you should give a URL to a 180px x 180px image hosted on imgur

The main class of your script must extend the Script class:

public final class ExampleScript extends Script

The Script class defines several useful methods, they can all be found on the API documentation here http://osbot.org/api/org/osbot/rs07/script/Script.html

It is abstract, it cannot be instantiated directly, you must subclass it, and override any abstract methods, in this case you must override the onLoop method.

The onLoop method is where all of the core functionality of your script will be called from:

```
@Override
public final int onLoop() throws InterruptedException {
    return 0;
}
```

The onLoop method is called repeatedly while your script is running, the delay between each time onLoop is called is defined by the integer value it returns. In the case of this example, the script executor would sleep for 0ms in between each onLoop call.
