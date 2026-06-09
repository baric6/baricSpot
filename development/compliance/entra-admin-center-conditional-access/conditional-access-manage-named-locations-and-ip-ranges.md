# Conditional Access Manage named locations and IP ranges

In Entra Admin center&#x20;

{% embed url="https://o365reports.com/2023/02/17/manage-named-locations-in-conditional-access-policies/" %}

#### Creating a named IP block policy

In Entra Admin center&#x20;

1. in the top search bar search for security

<figure><img src="../../../.gitbook/assets/image (476).png" alt=""><figcaption></figcaption></figure>

2. Click Security in the drop-down
3. &#x20;In the security tab on the left part of the tab click "Named Locations"

<figure><img src="../../../.gitbook/assets/image (478).png" alt=""><figcaption></figcaption></figure>

&#x20;4\. On the next page you will see countries and IP ranges location. For this we will pick the IP ranges

<figure><img src="../../../.gitbook/assets/image (479).png" alt=""><figcaption></figcaption></figure>

5. A fly-out window will appear what you need to fill out
   1. Give it a name
   2. Add a IP, the IP's should be structured as a cider notation
   3. At the top you should see upload and download
      1. Download -> will download a txt file with IP addresses&#x20;
      2. Upload -> will upload the file you downloaded with more or less IP depending what you want
         1. Note -> Append the IP's to the file it will wipe old data and replace with what is on the file&#x20;

<figure><img src="../../../.gitbook/assets/image (480).png" alt=""><figcaption></figcaption></figure>

6. Save and reload the page. When you see it it will be in A "not configured in any policy" state
   1. This means it is in report-only and not actually blocking anything

#### Set a conditional access policy to named locations&#x20;

1. After the named location is made you need to attach it to A conditional access policy&#x20;
2. Find the policy that you have made, with in that policy find the network button and add the named location to it&#x20;
3. save and now it you should see it under "Conditional Access Policies" Column
