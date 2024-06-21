# {15} Adding a GUI

GUIs (graphical user interfaces) for OSBot are written using the Java Swing library.

There are plenty of tutorials on how to use this library online, so I will only cover the basics here.

In this section I will show you how to create a simple woodcutting GUI, allowing the user to select a type of tree:

\-- placeholder for image of end result --

The first step to creating a GUI, is to create the top-level component, examples of which are JFrame, JDialog and JApplet.

For our GUIs we will be using the JDialog component.

There are two key reasons why we will be using JDialog:

1. We can set the JDialog to be a modal. A modal is a child window which appears in front of it's parent (In this case the OSBot application), and disables the parent window until the user's interaction with the modal is complete. This is useful if you want to prevent the script from running until the user has finished setting up everything in the GUI.
2. Best practice dictates that an application should not have more than one JFrame. Because OSBot already uses a JFrame, we should use something else for our child GUI.

JDialogs have both a content pane and a menu bar.

The content pane is where you will add the main interface of your GUI (labels, input boxes, check boxes, buttons etc.)

The menu bar isn't commonly used for OSBot GUIs, but you can make use of it for adding things like save / load / help options.

Creating a JDialog is simple:

```
import javax.swing.*;
import java.awt.*;

public class GUI {
    private final JDialog mainDialog;

    public GUI() {
        mainDialog = new JDialog();
        mainDialog.setTitle("Explv's Woodcutter");
        mainDialog.setModal(true);
        mainDialog.setModalityType(Dialog.ModalityType.APPLICATION_MODAL);
    }
}
```

In the above snippet I have created a class called GUI with one private member variable "mainDialog" which is of type JDialog. In the class' constructor I initialise the JDialog, set the title to "Explv's Woodcutter", and set the JDialog to be a modal. Because the JDialog is a modal, when it is open it will block input to all parent windows.

We can then add to the JDialog's content pane by calling:

```

mainDialog.getContentPane().add(...)

```

Or set the JDialog's menu bar:

```
mainDialog.setMenuBar(...);
```

Now we will define a couple of functions to open and close the GUI:

```
import javax.swing.*;
import java.awt.*;

public class GUI {
    private final JDialog mainDialog;

    public GUI() {
        mainDialog = new JDialog();
        mainDialog.setTitle("Explv's Woodcutter");
        mainDialog.setModal(true);
        mainDialog.setModalityType(Dialog.ModalityType.APPLICATION_MODAL);
    }

    public void open() {
        mainDialog.setVisible(true);
    }

    public void close() {
        mainDialog.setVisible(false);
        mainDialog.dispose();
    }
}
```

The open() function just sets the JDialog to be visible. The close() function sets the JDialog to not be visible, and then also calls dispose().

Now that we have a JDialog, we need to start thinking about it's layout and contents. Conveniently the Swing library provides you with an assortment of layout managers that handles the positioning and sizing of components for you. An overview of the different layout managers can be found here: https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html

DO NOT use an "absolute" layout (no layout manager). You will see many amateurs that are too lazy to understand the different layout managers and just resort to providing explicit x and y coordinates for each of their components. This will result in a GUI that is very fragile, cannot be resized, and is generally difficult to maintain. there is a reason why the layout managers exist, use them.

We can achieve a GUI where different parts use different layouts by using containers. The container you will be using most frequently is the JPanel. A JPanel is just an empty container, something which can have it's own layout and borders, that you can then add other components to.

For this GUI we will create a JPanel (empty container) with a vertical BoxLayout (the components are stacked vertically) as our main container. We will also add a 20px border, so that our components don't go right to the edge of the GUI:

```
import javax.swing.*;
import javax.swing.border.EmptyBorder;
import java.awt.*;

public class GUI {
    private final JDialog mainDialog;

    public GUI() {
        mainDialog = new JDialog();
        mainDialog.setTitle("Explv's Woodcutter");
        mainDialog.setModal(true);
        mainDialog.setModalityType(Dialog.ModalityType.APPLICATION_MODAL);

        JPanel mainPanel = new JPanel();
        mainPanel.setLayout(new BoxLayout(mainPanel, BoxLayout.PAGE_AXIS));
        mainPanel.setBorder(new EmptyBorder(20, 20, 20, 20));

        mainDialog.getContentPane().add(mainPanel);
    }

    public void open() {
        mainDialog.setVisible(true);
    }

    public void close() {
        mainDialog.setVisible(false);
        mainDialog.dispose();
    }
}
```

There are many components available in the Swing library, a visual guide to them can be found here: http://web.mit.edu/6.005/www/sp14/psets/ps4/java-6-tutorial/components.html

For this simple GUI, we will only be using a JLabel (for labelling things), a JComboBox (for selecting from a list of options), and a JButton (a button that when pressed will start the script)

The first thing we will add is a label that says "Select tree:", and a select box that contains different types of tree the user can choose from.

Because we want these two things to be grouped together in the GUI, I will create a JPanel to put both of them in:

```
JPanel treeSelectionPanel = new JPanel();
treeSelectionPanel.setLayout(new FlowLayout(FlowLayout.LEFT));
```

This JPanel uses a left aligned FlowLayout (components are placed in a row, if the width of the row is too small, components will be placed on multiple rows).

Now I will add the tree label to this panel:

```
JPanel treeSelectionPanel = new JPanel();
treeSelectionPanel.setLayout(new FlowLayout(FlowLayout.LEFT));

JLabel treeSelectionLabel = new JLabel("Select tree:");
treeSelectionPanel.add(treeSelectionLabel);
```

And finally I need to add the select box with different types of tree.

For the types of tree, I will be using an Enum. "An enum type is a special data type that enables for a variable to be a set of predefined constants. The variable must be equal to one of the values that have been predefined for it. Common examples include compass directions (values of NORTH, SOUTH, EAST, and WEST) and the days of the week."

The Enum will look like this:

```
enum Tree {
    NORMAL,
    OAK,
    WILLOW;
    
    @Override
    public String toString() {
        return name().toLowerCase();
    }
}
```

Note that in this Enum I am overriding the toString() function. Normally toString() would return the name of the Enum value e.g. "NORMAL" or "OAK". However having the name capitalised like that in the GUI is ugly, so I am returning the name in lowercase form.

Now I will create a select box with the different tree options and add it to our "treeSelectionPanel":

```
JPanel treeSelectionPanel = new JPanel();
treeSelectionPanel.setLayout(new FlowLayout(FlowLayout.LEFT));

JLabel treeSelectionLabel = new JLabel("Select tree:");
treeSelectionPanel.add(treeSelectionLabel);

JComboBox<Tree> treeSelector = new JComboBox<>(Tree.values());
treeSelectionPanel.add(treeSelector);
```

The selection panel is now complete, so I will add the selection panel to our "mainPanel".

The last component we need is a start button. When the user clicks this button, the GUI will close and the script will start, using the options that the user specified in the GUI:

```
JButton startButton = new JButton("Start");
startButton.addActionListener(e -> {
    started = true;
    close();
});
mainPanel.add(startButton);
```

We create a JButton with the text "Start", and we add an action listener to it. When the start button is clicked, the ActionListener will be called. The ActionListener just sets a global boolean variable called "started" to true, and then calls the close() function we defined, to close the GUI.

Finally, now that all of the components have been added to the JDialog, we need to "pack" it (resize all the components to their preferred sizes):

```
mainDialog.pack();
```

Now the GUI is complete. Note that in the following snippet I have added a boolean function isStarted() to return the value of the started boolean, and I have added a getSelectedTree() function to return the value of our tree selector. These functions exist so that they can be used from our script class:

```
import javax.swing.*;
import javax.swing.border.EmptyBorder;
import java.awt.*;

public class GUI {
    private final JDialog mainDialog;
    private final JComboBox<Tree> treeSelector;

    private boolean started;

    public GUI() {
        mainDialog = new JDialog();
        mainDialog.setTitle("Explv's Woodcutter");
        mainDialog.setModal(true);
        mainDialog.setModalityType(Dialog.ModalityType.APPLICATION_MODAL);

        JPanel mainPanel = new JPanel();
        mainPanel.setLayout(new BoxLayout(mainPanel, BoxLayout.PAGE_AXIS));
        mainPanel.setBorder(new EmptyBorder(20, 20, 20, 20));
        mainDialog.getContentPane().add(mainPanel);

        JPanel treeSelectionPanel = new JPanel();
        treeSelectionPanel.setLayout(new FlowLayout(FlowLayout.LEFT));

        JLabel treeSelectionLabel = new JLabel("Select tree:");
        treeSelectionPanel.add(treeSelectionLabel);

        treeSelector = new JComboBox<>(Tree.values());
        treeSelectionPanel.add(treeSelector);

        mainPanel.add(treeSelectionPanel);

        JButton startButton = new JButton("Start");
        startButton.addActionListener(e -> {
            started = true;
            close();
        });
        mainPanel.add(startButton);

        mainDialog.pack();
    }

    public boolean isStarted() {
        return started;
    }

    public Tree getSelectedTree() {
        return (Tree) treeSelector.getSelectedItem();
    }

    public void open() {
        mainDialog.setVisible(true);
    }

    public void close() {
        mainDialog.setVisible(false);
        mainDialog.dispose();
    }
}

enum Tree {
    NORMAL,
    OAK,
    WILLOW;

    @Override
    public String toString() {
        return name().toLowerCase();
    }
}

```

Now we need to integrate the GUI into our Script:

```
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;

import javax.swing.*;
import java.lang.reflect.InvocationTargetException;

@ScriptManifest(author = "Explv", name = "Explv's Woodcutter", info = "", version = 0.1, logo = "")
public class ExampleScript extends Script {

    private GUI gui = new GUI();
    private Tree tree;

    @Override
    public void onStart() {
        try {
            SwingUtilities.invokeAndWait(() -> {
                gui = new GUI();
                gui.open();
            });
        } catch (InterruptedException | InvocationTargetException e) {
            e.printStackTrace();
            stop();
            return;
        }
        
        // If the user closed the dialog and didn't click the Start button
        if (!gui.isStarted()) {
            stop();
            return;
        }
        
        tree = gui.getSelectedTree();
    }

    @Override
    public int onLoop() throws InterruptedException {
        // go and chop down tree   
        return 600;
    }
    
    @Override
    public void onExit() {
        if (gui != null) {
            gui.close();
        }
    }
}

```

In the onStart() function we create an instance of our GUI, and we open it. Note that any Swing operation should be performed on the EDT (Event dispatching thread). To do this, we call SwingUtilities.invokeAndWait(Runnable runnable):

```
try {
    SwingUtilities.invokeAndWait(() -> {
        gui = new GUI();
        gui.open();
    });
} catch (InterruptedException | InvocationTargetException e) {
    e.printStackTrace();
    stop();
    return;
}
```

Once the GUI is closed we check that the user actually clicked the start button (isStarted() would return true). If they didn't click the start button, and just closed the window, we don't want to start the script because the user didn't set it up correctly. So we just call stop().

```
if (!gui.isStarted()) {
    stop();
    return;
}
```

Otherwise if the user did start the script using the start button, we can retrieve the selected Tree from the GUI and then begin our woodcutting script:

```
tree = gui.getSelectedTree();
```
