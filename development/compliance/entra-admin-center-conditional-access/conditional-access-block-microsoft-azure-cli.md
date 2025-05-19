# Conditional Access block Microsoft Azure CLI

**Using the Azure Portal:**

1. **Sign in to the Azure portal** as at least a Conditional Access Administrator.
2. Navigate to **Microsoft Entra ID** > **Security** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a **Name**.
5. Under **Assignments**, select **Users or workload identities**.
   * Choose who the policy will apply to (e.g., All users, specific groups).
   * It's recommended to **Exclude** emergency access or break-glass accounts.
6. Under **Target resources** > **Cloud apps** > **Include**, select **Select apps**.
   * Search for and select **Windows Azure Service Management API**. This service principal represents the Azure Resource Manager and includes access via the Azure CLI.
7. Under **Access controls** > **Grant**, select **Block access**, and then click **Select**.
8. **Confirm your settings** and set **Enable policy** to **On**. (It's often recommended to start in **Report-only** mode to assess the impact before fully enabling).
9. Select **Create**.

**What this policy does:**

This policy targets the "Windows Azure Service Management API," which is the underlying API used by the Azure CLI to manage Azure resources. By blocking access to this API, you effectively prevent users within the scope of the policy from logging in using the Azure CLI.

**Important Considerations:**

* **Impact:** Blocking access to the "Windows Azure Service Management API" will prevent users from managing Azure resources through the Azure CLI. Ensure this aligns with your organization's needs and that affected users have alternative methods for management, if required.
* **Exclusions:** Carefully consider excluding administrative accounts or break-glass accounts from this policy to prevent accidental lockout scenarios.
* **Report-only mode:** Before fully enabling the policy, use the "Report-only" mode to monitor the potential impact on users' sign-in attempts. This allows you to identify any unintended consequences.
* **Service Principals and Managed Identities:** Conditional Access policies targeting users do not apply to service principals or managed identities. If you need to restrict their access, you would need to create separate Conditional Access policies for workload identities.

By implementing this Conditional Access policy, you can effectively control and block Azure CLI logins for specific users or groups within your organization.
