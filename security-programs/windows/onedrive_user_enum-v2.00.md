# Onedrive\_user\_enum v2.00

enumerate valid onedrive users In this instance, the username is 'lightmand' and the domain is 'acmecomputercompany.com'. If a user has logged into OneDrive, this path will exist and return a 403 status code. If they have not, or the user is invalid, it will return a 404.

The results may vary depending on how widely used OneDrive is within an org. Currently it is the most reliable user-enumeration method that I'm aware of (office365userenum no longer works, and the others like UhOh365 are unreliable). Further, it does not attempt a login and is much more passive, and should be undetectable to the target org. Microsoft will see the hits, but the target org won't.

Site&#x20;

{% embed url="https://www.trustedsec.com/blog/onedrive-to-enum-them-all/" %}

Download&#x20;

{% embed url="https://github.com/nyxgeek/onedrive_user_enum" %}
