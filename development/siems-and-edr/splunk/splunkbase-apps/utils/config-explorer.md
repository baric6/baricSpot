# Config explorer

This app provides a editor interface for viewing and editing Splunk files. It has the following features:

* Code completion and tooltip hinting for '.conf' files (by loading the Splunk '.spec' files)
* Code gutter highlights if the line can be found in btool and if it is valid according to spec files
* Displays the spec files relevant to your Splunk installation
* Diff files
* Provides a syntax-highlighted interface to btool, and allows diffing against the currently running config
* Embeds the excellent Microsoft Monaco editor (Visual Studio Code) - with three themes
* Provides useful developer hooks (bump, debug refresh etc) that can be customised and extended
* Optional version control of all changes by committing them to a git repository before and after changes
* Works on Linux and Windows (it is quite slow on Windows)

By default, the app is not able to save files, but this can be enabled from the "Settings" link. As this app provides unrestricted access to Splunk files, users must have the "admin" role to see the app.

<figure><img src="../../../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://splunkbase.splunk.com/app/4353" %}
