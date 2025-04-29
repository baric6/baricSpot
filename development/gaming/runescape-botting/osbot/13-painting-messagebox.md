# {13} Painting, messagebox

You can add a paint to your script using one of two methods:

* By overriding the onPaint method in the Script class (this method is available because the Script class implements the Painter interface):

```
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

import java.awt.*;

@ScriptManifest(name = "Paint example", author = "Explv", info = "", version = 0.1, logo = "")
public class PaintExample extends Script {

    @Override
    public int onLoop() throws InterruptedException {
        return 0;
    }
    
    @Override
    public void onPaint(final Graphics2D g) {
        // Add painting code here
    }
}
```

Or by creating a class that implements the Painter interface, and then adding a new instance of your painter when the script starts using the addPainter method in the Bot class:

```
import org.osbot.rs07.canvas.paint.Painter;
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

import java.awt.*;

@ScriptManifest(name = "Paint example", author = "Explv", info = "", version = 0.1, logo = "")
public class PaintExample extends Script {

    @Override
    public void onStart() {
        getBot().addPainter(new Paint());
    }
    
    @Override
    public int onLoop() throws InterruptedException {
        return 0;
    }
}

class Paint implements Painter {
    
    @Override
    public void onPaint(Graphics2D g) {
        
    }
}
```

To paint text, shapes etc. simply call methods found in the Graphics2D class

For examples of things you can paint onScreen see my other tutorial
