# Conditional Access - Block unknown or unsupported device platform

### Block Generic Devices Like Windows, Linux, Mac

{% embed url="https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-unknown-unsupported" %}

### Block Device OS type like Window 7, XP ...

1. **Sign in to Microsoft Entra Admin Center**
   * Navigate to **Protection → Conditional Access**.
   * Click **+ New policy**.
2. **Name the Policy**
   * Give the policy a name, e.g., **"Block Unsupported Windows Devices"**.
3. **Assignments → Users**
   * Select **All Users** (or specific groups/users if necessary).
4. **Assignments → Cloud Apps or Actions**
   * Select **All cloud apps** (or choose specific apps you want to protect).
5. **Assignments → Conditions**
   * Under **Device platforms**, select **Windows**.
   * Under **Device filters**, enable **Filter for devices** and configure:
     * **Property**: `device.operatingSystem`
     * **Operator**: `contains`
     * **Value**: `Windows 7` (also add `Windows XP` if needed).
6. **Access Controls → Grant**
   * Select **Block access**.
7. **Enable Policy**
   * Set the **Enable policy** option to **On**.
   * Click **Create** to enforce the policy.



This **Conditional Access Policy** would block:

1. **All Windows 7 Devices** – Any user trying to sign in from a Windows 7 device will be denied access.
2. **Older Windows Versions** – If you extend the filter (`Windows XP`, `Windows 8`), those will also be blocked.
3. **Any App Targeted by the Policy** – If you applied it to **all cloud apps**, it will block access to services like:
   * **Microsoft 365 Apps** (Outlook, Teams, SharePoint, OneDrive)
   * **Azure Virtual Desktop**
   * **Other Entra ID-protected services**

#### **What It Won’t Block**

* **Devices Not Enrolled in Entra ID**: If the device isn't registered, it may not be evaluated properly.
* **Users with Exemptions**: If you exclude users (e.g., admins), they won’t be affected.
* **Personal Devices (If Not Registered)**: Unless you're enforcing device registration, unmanaged personal devices might bypass this.
