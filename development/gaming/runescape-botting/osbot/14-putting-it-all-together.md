# {14} Putting it all together

This script will be a simple Al-kharid iron bar smelter.

First, I will write some pseudocode:

```
if the inventory contains iron ore:
    if the player is in the smelting room:
        if the what would you like to smelt widget is visible:
            if interact with the iron bar widget with the Smelt X interaction successful:
                sleep until the enter amount dialog is visible
        else if the enter amount dialog is visible:
            if enter the amount successful:
                sleep until the inventory does not contain iron ore, or until the player levels up
        else:
            interact with the furnace
else if the player is not in the bank:
    walk to the bank
else if the bank is not open:
    open the bank
else if the inventory contains an item that is not iron ore:
    deposit all
else if the bank contains iron ore:
    withdraw all iron ore
else:
    logout and stop the script
```

Now to convert this into Java:

```
import org.osbot.rs07.api.map.Area;
import org.osbot.rs07.api.map.constants.Banks;
import org.osbot.rs07.api.ui.RS2Widget;
import org.osbot.rs07.script.MethodProvider;
import org.osbot.rs07.script.Script;
import org.osbot.rs07.script.ScriptManifest;
import org.osbot.rs07.utility.ConditionalSleep;

import java.util.function.BooleanSupplier;

@ScriptManifest(name = "Iron smelter", author = "Explv", info = "Smelts iron bars in Al-kharid", version = 0.1, logo = "")
public final class IronSmelter extends Script {

    private final Area smeltingRoom = new Area(3279, 3184, 3272, 3188);

    @Override
    public final int onLoop() throws InterruptedException {
        if (canSmeltIronBars()) {
            smelt();
        } else {
            bank();
        }
        return random(150, 200);
    }

    private void smelt() {
        if (!smeltingRoom.contains(myPosition())) {
            getWalking().webWalk(smeltingRoom);
        } else if (isSmeltScreenVisible()) {
            if (smeltXIron()) {
                Sleep.sleepUntil(this::isEnterAmountPromptVisible, 3000);
            }
        } else if (isEnterAmountPromptVisible()) {
            if (enterRandomAmount()) {
                Sleep.sleepUntil(() -> !canSmeltIronBars() || getDialogues().isPendingContinuation(), 100_000);
            }
        } else if (useFurnace()) {
            Sleep.sleepUntil(this::isSmeltScreenVisible, 5000);
        }
    }

    private boolean canSmeltIronBars() {
        return getInventory().contains("Iron ore");
    }

    private boolean useFurnace() {
        return getObjects().closest("Furnace").interact("Smelt");
    }

    private boolean isSmeltScreenVisible() {
        return getWidgets().getWidgetContainingText("What would you like to smelt?") != null;
    }

    private boolean smeltXIron() {
        return getWidgets().getWidgetContainingText("Iron").interact("Smelt X Iron");
    }

    // Using a custom filter here instead of getWidgetContainingText() because it ignores widgets with root id 162
    private boolean isEnterAmountPromptVisible(){
        RS2Widget amountWidget = getWidgets().singleFilter(getWidgets().getAll(), widget -> widget.getMessage().contains("Enter amount"));
        return amountWidget != null && amountWidget.isVisible();
    }

    private boolean enterRandomAmount() {
        return getKeyboard().typeString("" + MethodProvider.random(28, 99));
    }

    private void bank() throws InterruptedException {
        if (!Banks.AL_KHARID.contains(myPosition())) {
            getWalking().webWalk(Banks.AL_KHARID);
        } else if (!getBank().isOpen()) {
            getBank().open();
        } else if (!getInventory().isEmptyExcept("Iron ore")) {
            getBank().depositAll();
        } else if (getBank().contains("Iron ore")) {
            getBank().withdrawAll("Iron ore");
        } else {
            stop(true);
        }
    }
}

class Sleep extends ConditionalSleep {

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
