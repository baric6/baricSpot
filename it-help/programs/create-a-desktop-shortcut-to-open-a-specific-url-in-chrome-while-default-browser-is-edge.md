# Create a desktop shortcut to open a specific URL in Chrome while default browser is Edge

#### Steps to Create a Desktop Shortcut to Open a Link in Chrome:

1. **Right-click on your desktop** and select **New > Shortcut**.
2. In the **"Create Shortcut"** window that opens, in the location field, enter:
   1. Note - Right click to make a desktop shortcut (had troubles other way)
   2. Note - When copying the below link it may append another "C:\ , if it does just delete the inner C: and it should work

```
"C:\Program Files\Google\Chrome\Application\chrome.exe" https://www.example.com
```

Replace `https://www.example.com` with the link you want to open.

3. Click **Next**, then give your shortcut a name (e.g., "Open Link in Chrome").
4. Click **Finish**.

Now, when you double-click the shortcut, it will open the specified URL in Google Chrome, even if Chrome is not your default browser.

If Chrome is installed in a different location, make sure to adjust the path to `chrome.exe` accordingly.
