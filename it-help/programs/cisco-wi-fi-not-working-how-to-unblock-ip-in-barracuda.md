# Cisco Wi-Fi not working how to Unblock IP in barracuda

## Login to your Meraki portal

1. Search for your location you want to view the access points
2. To find the access points go to Wireless > Overview this will show you the health of the data coming out of the access points

<figure><img src="../../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

3. If you are seeing nothing but good it is probably getting blocked by a firewall or content shield
4. Under wireless > SSID's > find your guest network > click edit settings
5. In this menu scroll down to the DNS IP section check if thoses are your correct DNS IPS
6. Now in the Meraki portal under the store location you picked before find the public IP for the network under security and SD-WAN scroll down to wan1 and wan2

<figure><img src="../../.gitbook/assets/image (167).png" alt=""><figcaption></figcaption></figure>

7. Now open barracuda and navigate to the content shield then to DNS Filtering



8. Hit the 3 dots at the end of the location and select edit
9. A window will pop up saying network

<figure><img src="../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

10. Add the outbound address you found as the wan1 and wan2 and hit "ADD OUTBOUND IP ADDRESS" the hit save
11. After about 30 mins guest network should have Internet connectivity
