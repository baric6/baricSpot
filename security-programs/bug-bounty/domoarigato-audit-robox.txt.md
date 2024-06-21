# DomoArigato audit robox.txt

A simple command line tool which quickly audits the Disallow entries of a site's robots.txt. Disallow entries can be used to stop search engines from indexing specific directories and files. Thus, sometimes it can be an easy way to find pages that it's worthwhile for the user to check out.

Domo will run through every Disallow entry, visit the page and return the HTTP Status Code. If any return 200, it means you'll be able to visit it.

You can also choose to search bing.com to see if the page has been indexed, and web.archive.org to see if it's been archived.

{% embed url="https://github.com/EmberHext/DomoArigato" %}
