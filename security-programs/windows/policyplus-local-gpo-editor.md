# Policyplus local gpo editor

At startup, Policy Plus opens the last saved policy source, or the local Group Policy Object (Local GPO) by default. To open a different policy source (like a Registry branch or a per-user GPO), use File | Open Policy Resources.

Much like the official Group Policy editor, categories are shown in the left tree. Information on the selected object is shown in the middle. Policies and subcategories in the selected category are shown in the right list. By default, both user and computer policies are displayed, but you can focus on just one policy source using the drop-down in the upper left.

To edit a policy, double-click it. If the selected setting applies to both users and computers, you can switch sections with the "Editing for" drop-down. Click OK to keep the changes to the setting. Notice: If a policy source is backed by a POL file (like Local GPO), changes to it will not be committed to disk until you use File | Save Policies (Ctrl+S).

Download&#x20;

{% embed url="https://github.com/Fleex255/PolicyPlus" %}
