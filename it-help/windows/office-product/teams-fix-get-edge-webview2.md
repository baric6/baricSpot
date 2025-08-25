# (Teams) -fix- Get Edge WebView2

<figure><img src="../../../.gitbook/assets/cd558468-0a4e-4a61-baa6-291eb3fa7aa9.jpg" alt=""><figcaption></figcaption></figure>

Issue:

The user reported that after a Windows rollback to the 23H2 update, the microphone issue was resolved, but Microsoft Teams failed to launch with an error message: "We've run into an issue. We can't find a required component to run Teams. Download and install it, and then try opening Teams again." The error suggested downloading and installing Edge WebView2, but the download failed, indicating WebView2 was already installed on the system. Teams could not open due to this issue.

Steps Taken:

Initial Investigation:

1. Attempted to launch Microsoft Teams, and the error message indicated a missing component, WebView2.
2. Clicking on the "Get Edge WebView2" button did not work initially.
3. When navigating manually to the WebView2 download page, the download failed with the message that WebView2 was already installed on the computer.

Troubleshooting:

The WebView2 component is often embedded and does not show up in the Apps list.

Uninstalling and reinstalling Microsoft Teams did not resolve the issue.

Restarting the system also did not help in resolving the error.

Solution Found and Applied:

After further research, it was determined that a registry entry could be causing the conflict with WebView2.

The following steps were executed to fix the issue:

Solution Steps:

1. Open Registry Editor (regedit).
2. Navigate to the following registry path: Computer\HKEY\_LOCAL\_MACHINE\SOFTWARE\WOW6432Node\Microsoft\EdgeUpdate\Clients\\
3. Under the Clients folder, find and delete the folder with the name: {F3017226-FE2A-4295-8BDF-00C3A9A7E4C5}.
4. After deleting this registry folder, run the WebView2 installer to reinstall WebView2.
5. Once WebView2 is reinstalled, Microsoft Teams launched successfully without issues.

Outcome:

After following the above steps, Microsoft Teams launched successfully, and the WebView2 error was resolved. The user is now able to use Teams without any issues.
