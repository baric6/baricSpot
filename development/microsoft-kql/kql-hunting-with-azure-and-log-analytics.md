# KQL hunting with Azure and Log Analytics

**Large number of failed authentications** - If a user account has a large amount of failed authentications in a short time period, it could be a sign of a brute force or password spray attack. The following KQL example will return all users that have 10+ failed password attempts in the last 24 hours.

```
SigninLogs
| where TimeGenerated > ago (24hrs)
| where ResultType == "50126"
| summarize event_count = count() by UserPrincipalName 
| where event_count > 9
| project UserPrincipalName, event_count
```



**MFA fatigue attack** - An MFA fatigue attack is where the end user is repeatedly bombarded with MFA requests in the hope they will approve one. The number match experience has largely mitigated this type of attack but **this is also an indicator that a user's password may have been compromised so needs to be reviewed urgently.** The following KQL example will return users that have had 5+ MFA failures or device authentication failures in the last 24 hours.

```
SigninLogs
| where TimeGenerated > ago (24hrs)
| where ResultType == "500121" or ResultType == "50155" or ResultType == "50158"
| summarize event_count = count() by UserPrincipalName 
| where event_count > 4
| project UserPrincipalName, event_count
```



**MFA fraud** - If a user reports MFA fraud via authenticator app\phone then it's possible that the user has received an MFA challenge that they did not initiate. This could be a sign that the user's password has been compromised and a MFA fatigue attack is underway. The following KQL example will return users that have either denied MFA or reported fraud.

```
SigninLogs
| where TimeGenerated > ago (24hrs)
| where Status contains "MFA denied" or Status contains "Fraud"
| summarize by UserPrincipalName, tostring (Status.additionalDetails)
```



**Account locked out** - If a user's account has been locked out (smart lock out) it could indicate that sign-in attempts have come from a known malicious IP address, or the account was locked due to repeated sign-in attempts. The following KQL example will return users that have had their account locked out.&#x20;

```
SigninLogs
| where TimeGenerated > ago (24hrs)
| where ResultType == "50053"
| summarize count() by UserPrincipalName
```



**Users successfully authenticating to external Entra ID tenants** - If your organization doesn't allow (or tightly controls) access to external Entra ID tenants then you can monitor this. This KQL example shows the user and tenantID of the resource tenant they accessed.

```
 SigninLogs
| where TimeGenerated > ago (24hrs)
| where AADTenantId != ResourceTenantId
| where ResultType == "0"
| summarize count() by UserPrincipalName, ResourceTenantId
```



**Users that have put in the correct passwords but failed the MFA and are risky users**

```
SigninLogs
| where TimeGenerated >= ago(7d)
| where AuthenticationDetails contains '"Correct password' and Status contains "Failure" and RiskState == "atRisk"
| project
    TimeGenerated,
    Identity,
    Location,
    AuthenticationDetails,
    AuthenticationRequirement,
    Status,
    RiskEventTypes,
    RiskEventTypes_V2,
    RiskLevelAggregated,
    RiskLevelDuringSignIn,
    RiskState,
    ConditionalAccessStatus,
    OperationName,
    ResultType,
    ResultDescription,
    ClientAppUsed,
    ConditionalAccessPolicies,
    DeviceDetail,
    Id,
    IPAddress,
    LocationDetails,
    AppDisplayName,
    ResourceDisplayName,
    UserAgent
```



**Users that are risky**

```
SigninLogs
| where TimeGenerated >= ago(7d)
| where RiskState == "atRisk"
| project
    TimeGenerated,
    Identity,
    Location,
    AuthenticationDetails,
    AuthenticationRequirement,
    Status,
    RiskEventTypes,
    RiskEventTypes_V2,
    RiskLevelAggregated,
    RiskLevelDuringSignIn,
    RiskState,
    ConditionalAccessStatus,
    OperationName,
    ResultType,
    ResultDescription,
    ClientAppUsed,
    ConditionalAccessPolicies,
    DeviceDetail,
    Id,
    IPAddress,
    LocationDetails,
    AppDisplayName,
    ResourceDisplayName,
    UserAgent
```
