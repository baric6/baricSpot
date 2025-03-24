# Delaying a service starting in Microsoft

To delay a service start in Windows, set its startup type to "Automatic (Delayed Start)" in the Services console, which will cause the service to start a few minutes after boot. Here's a more detailed explanation:How to Set a Service to "Automatic (Delayed Start)"

1. **Open the Services Console:** Press the Windows key + R to open the Run window, type `services.msc`, and press Enter.&#x20;
2. **Locate the Service:** Find the service you want to delay in the list.&#x20;
3. **Open Service Properties:** Double-click the service to open its properties window.&#x20;
4. **Change Startup Type:** In the General tab, select "Automatic (Delayed Start)" from the Startup type drop-down.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

1. **Save Changes:** Click OK to save the changes.&#x20;
