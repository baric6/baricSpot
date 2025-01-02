# (bugbounty) Wildcrawl

<figure><img src="../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>

Here's a summary of what the script does:

* Crawls the target URL using Hakrawler .
* Removes duplicate links.
* Extracts all files of certain types (e.g., PDF, DOC, ZIP, JPG) and saves them to a separate file.
* Extracts all domains and removes duplicates.
* Filters out certain domains (e.g., Facebook, Twitter, LinkedIn).
* Extract records of each domain.
* Gets all the IPs associated with the filtered domains.
* Extracts the title of each domain and IP.
* Filters out any results that have a title starting with "404".

At the end you will have these files saved in "scan\_1, scan\_2, etc.";

{% embed url="https://github.com/NeverWonderLand/wildcrawl" %}
