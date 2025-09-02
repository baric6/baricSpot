# IOS 12.5.7

Resources&#x20;

{% embed url="https://ios.cfw.guide/installing-chimera/#rejailbreaking-with-totallynotspyware-v2-a10-x-and-earlier" %}

Chimera is a [semi-untethered jailbreak](https://ios.cfw.guide/types-of-jailbreak/#semi-untethered-jailbreaks), meaning it requires an app or website to re-apply the exploit after a reboot.

Chimera is capable of jailbreaking all devices on iOS 12.0 to 12.1.2 and A7 to A11 devices on iOS 12.0 to 12.5.7.

Due to how semi-untethered jailbreaks work, if you are using an A11 or newer device, the app will need to be [re-signed](https://ios.cfw.guide/resigning-apps) once every 7 days.

We will use Sideloadly to install the Chimera jailbreak application to your iOS device for use in the next step.

If you have a newer device with an A12 SoC, such as the iPhone XS, you can only use Chimera on iOS 12.0 - 12.1.2. If you are on iOS 12.1.3 to 12.4.1, you will need to follow [Installing unc0ver](https://ios.cfw.guide/installing-unc0ver) instead.

If you are already jailbroken with another jailbreak (besides Odysseyra1n), make sure to properly [remove it](https://ios.cfw.guide/restoring-rootfs) before proceeding.

### &#x20;<a href="#downloads" id="downloads"></a>

### Downloads <a href="#downloads" id="downloads"></a>

* The latest release of [Chimera](https://chimera.coolstar.org/)
* A7 or A8(X) devices running either 12.3.x or 12.4.1 to 12.5.7 are recommended to use [Chimera patched with chimera\_patch](https://jailbreaks.app/cdn/ipas/ChimeraPatch-resigned.ipa)
*
  * for improved success rates.
* The latest version of [Sideloadly](https://sideloadly.io/)

The latest version of [iTunes](https://www.apple.com/itunes/download/win64)

* if on Windows.

The patched version of Chimera recommended above is an _unofficial build_ of Chimera patched with staturnz's [chimera\_patch](https://github.com/staturnzz/chimera_patch)

to improve success rate on older devices.

The unofficial build is **completely unnecessary** on newer (A9 and later) devices. Additionally, if you're not comfortable using an unofficial build of Chimera, the normal build of Chimera will still work.

![A screenshot of the Sideloadly application (Windows)](https://ios.cfw.guide/assets/images/sideloadly_win.png)

### &#x20;<a href="#installing-the-application" id="installing-the-application"></a>

### Installing the application <a href="#installing-the-application" id="installing-the-application"></a>

1. Open Sideloadly
2. Plug your iOS device into your computer
   * Make sure your computer is trusted and allowed to view the contents of your device
3. Drag and drop the Chimera `.ipa` file into Sideloadly
4. Enter in your Apple Account
5. Enter in your password

The app will now install to your iOS device.

### &#x20;<a href="#trusting-the-application" id="trusting-the-application"></a>

### Trusting the application <a href="#trusting-the-application" id="trusting-the-application"></a>

1. Go to `Settings` -> `General` -> `Device Management` -> `<Your Apple Account>`
   * Depending on your usage, `Device Management` may be labeled `Profiles and Device Management`
2. Tap `Trust "<Your Apple Account>"`

The Chimera application can now be opened from home screen.

### &#x20;<a href="#running-chimera" id="running-chimera"></a>

### Running Chimera <a href="#running-chimera" id="running-chimera"></a>

1. Reboot your phone
   * This is not necessary but recommended
2. Open the Chimera application from your home screen immediately afterwards
3. Tap "Jailbreak"
4. Reboot your phone again when prompted
   * If you are not prompted and it automatically reboots, wait 1-2 minutes, then try again.
   * This time, it is necessary
5. Once again, open the Chimera application from your home screen immediately after rebooting
6. Tap "Jailbreak" again
   * If it automatically reboots or crashes and the jailbreak is not installed, wait 1-2 minutes, then try again.

If that app or your device continually crashes/restarts unexpectedly and the jailbreak isn't installed despite the above steps, attempt to put the device in a freezer for that 1-2 minute period.

You should now be jailbroken with Sileo installed on your home screen. You can use Sileo to install [tweaks](https://ios.cfw.guide/faq/#what-are-tweaks), themes and more.

### &#x20;<a href="#installing-necessary-software" id="installing-necessary-software"></a>

### Installing necessary software <a href="#installing-necessary-software" id="installing-necessary-software"></a>

1. Open the Sileo application
2. Tap on the "Search" tab
3. Search for "libiosexec1"
4. Tap "Modify", then Tap "Upgrade"
5. Tap the "Queued" bar at the bottom of the page
6. Tap "Confirm"
7. Once finished, tap "Done"
8. Search for "libhooker (common)", "PreferenceLoader", and "RocketBootstrap" and add them to the queue by pressing "Install"
   * While we're preparing the queue, do not install the anything that is queued until after we've selected all our programs to install
9. Tap the "Queued" bar at the bottom of the page
10. Tap "Confirm"
11. Once finished, tap 'Restart SpringBoard'

### &#x20;<a href="#rejailbreaking-with-totallynotspyware-v2-a10-x-and-earlier" id="rejailbreaking-with-totallynotspyware-v2-a10-x-and-earlier"></a>

### Rejailbreaking with TotallyNotSpyware-v2 (A10(X) and earlier) <a href="#rejailbreaking-with-totallynotspyware-v2-a10-x-and-earlier" id="rejailbreaking-with-totallynotspyware-v2-a10-x-and-earlier"></a>

Rejailbreaking with TotallyNotSpyware-v2 is only supporting on A10(X) and earlier devices. A11 and later devices will need to keep the Chimera app resigned in order to rejailbreak.

As Chimera is a semi-untethered jailbreak, you won't remain jailbroken if your device reboots or powers off for any reason. Luckily, on A10(X) and earlier devices, rather than needing to keep the Chimera app sideloaded, you can simply follow the below steps to rejailbreak your device.

This **does not** install the jailbreak in the first place - you'll need to sideload the Chimera app and jailbreak normally first before being able to follow this section.

1. Open Safari on your iOS device
2. Go to the [jbme.h4ck.kr](http://jbme.h4ck.kr)
3. website, and tap `re-jailbreak`
4. When prompted, press `Close` on any prompts that appear within Safari
5. Tap `userspace reboot` to complete the rejailbreaking process

If you get `The webpage was reloaded because a problem occurred`, fully close Safari through the App Switcher, then reopen Safari, refresh the page, and try again.

Your device should now be in a jailbroken state again.
