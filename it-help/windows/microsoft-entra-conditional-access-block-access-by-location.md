# Microsoft Entra conditional access: block access by location

{% embed url="https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-policy-location" %}

#### **Step 1: Create a Conditional Access Policy to Block Non-US Access**

1. **Go to Azure AD:**
   * Sign in to the Azure portal: [https://portal.azure.com](https://portal.azure.com)
   * Navigate to **Azure Active Directory** > **Security** > **Conditional Access**.
2. **Create a New Policy:**
   * Click on **+ New policy**.
3. **Set Assignments:**
   * **Users or workload identities**:
     * Select **Specific users** and choose the target user(s).
   * **Cloud apps or actions**:
     * Choose **All cloud apps** to block access globally.
   * **Conditions**:
     * Under **Locations**:
       * Click **Configure** > Select **Yes**.
       * Under **Include**, select **Any location**.
       * Under **Exclude**, click **Selected locations** > Select **United States** (you need to create a named location for the US if it doesn’t exist).
4. **Define Access Controls:**
   * Under **Grant**, select **Block access**.
5. **Enable the Policy:**
   * Set **Enable policy** to **On** and click **Create**.
