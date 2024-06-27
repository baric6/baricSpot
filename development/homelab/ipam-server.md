# ipam server

Applies to: Windows Server 2022, Windows Server 2019, Windows Server 2016. IP Address Management (IPAM) is an integrated suite of tools to enable end-to-end planning, deploying, managing and monitoring of your IP address infrastructure, with a rich user experience

### Video

{% embed url="https://www.youtube.com/watch?v=8qoAfsAzrew" %}

### basic steps

1. ipam is best as a seprate vm
2. make sure you sign in as domain user with admin privs
3. in your server flavor under roles and features find ipam under the feature section
4. install
5. under ipam settings under overview in the middle section go through each to setup
6. under the section server inventory after you set up all you will see that the ipam server has no privs
7. run command Invoke-IpamGpoProvisioning -Domain cyberpunk.local -GpoPrefixName IPAM -IpamServerFqdn iis.cyberpunk.local
8. refresh and you should see a green checkmark
