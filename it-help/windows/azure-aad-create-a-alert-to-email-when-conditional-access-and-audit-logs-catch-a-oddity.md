# Azure AAD create a alert to email when conditional access and Audit logs catch a oddity

#### **Step 2: Set Up Alerts to Notify Users of Blocked Sign-Ins**

Azure AD logs Conditional Access sign-in events, which you can monitor and send alerts via **Azure Monitor** and **Log Analytics**.

**A. Enable Diagnostic Settings for Azure AD Sign-In Logs**

1. Go to **Azure Active Directory** > **Monitoring** > **Diagnostic settings**.
2. Click **+ Add diagnostic setting**.
3. Select **SignInLogs** and send logs to a **Log Analytics workspace** or **Azure Monitor**.

**B. Create an Alert Rule in Azure Monitor**

1. **Navigate to Azure Monitor:**
   * Go to the **Azure portal** > **Monitor** > **Alerts**.
2. Click **+ Create** > **Alert rule**.
3. **Set Scope**:
   * Select the Log Analytics workspace where you’re sending Azure AD Sign-In Logs.
4. **Add a Condition**:
   * Click **Add condition**.
   * Select **Custom log search**.
   * Use the following **KQL Query** to detect blocked sign-ins outside the US:

```bash
SigninLogs
| where ConditionalAccessStatus == "failure"
| where Status.errorCode == 53003  // Blocked by Conditional Access
| where Location != "United States"
```



* Adjust filters to your needs, including user names.

5. **Configure Actions to Send Email**:

* Under **Actions**, create an **action group**.
* Add **Email/SMS/Push/Voice** action type.
* Provide the user’s email address to notify them.

6. **Set Alert Rule Name and Severity**:

* Name the alert rule and set the severity (e.g., **High**).

6. Save the alert.
