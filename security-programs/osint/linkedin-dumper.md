# Linkedin Dumper



<figure><img src="../../.gitbook/assets/image (218).png" alt=""><figcaption></figcaption></figure>

linkedInDumper is a Python 3 script that dumps employee data from the LinkedIn social networking platform.

The results contain firstname, lastname, position (title), location and a user's profile link. Only 2 API calls are required to retrieve all employees if the company does not have more than 10 employees. Otherwise, we have to paginate through the API results. With the --email-format CLI flag one can define a Python string format to auto generate email addresses based on the retrieved first and last name.

Download&#x20;

{% embed url="https://github.com/l4rm4nd/LinkedInDumper" %}
