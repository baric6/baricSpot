# Clear Windows Creds

When you try to access protected file shares on the network or launch RDP sessions, you’ll be prompted to save the passwords. If you checked the option to remember your credentials, Windows will store your passwords for the next connection.

<figure><img src="../../../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>

In this tutorial we’ll show you 2 simple ways to clear saved credentials for network share, remote desktop connection or mapped drive in Windows 10 / 8 / 7. Method 1: Clear Network Saved Credentials Using Control Panel

1. Open the Control Panel and select Large icons in the View by menu. Click User Accounts.

<figure><img src="../../../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

2. Click the “Manage your credentials” option at the top left.

<figure><img src="../../../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>

3. Select the Windows Credentials type and you’ll see the list of credentials you have saved for network share, remote desktop connection or mapped drive.

<figure><img src="../../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

4. Click one of the entries in the list and expand it, you can then click the Remove option to clear it.

## Method 2: Clear Network Saved Credentials Using the Run Command

1. Press the Windows key + R together to open the Run box. Type the following command and hit Enter. rundll32.exe keymgr.dll, KRShowKeyMgr

<figure><img src="../../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

2. You’ll see the Stored Usernames and Passwords window. To remove a saved network credential you can select one of the entries and click Remove.

<figure><img src="../../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

That’s it!
