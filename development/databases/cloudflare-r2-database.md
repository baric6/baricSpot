# Cloudflare R2 Database

#### Create a free account at:

{% embed url="https://www.cloudflare.com/" %}

\*Note&#x20;

* You will have to put a some kind of card in to make a account they wont charge you unless you do not pick the free one.

#### Database&#x20;

1. When in your profile go to quick search on the page, should be some where obvious&#x20;
2. Find "R2 Object Storage"
3. There is a blue button saying "+ Create bucket" click it
4. Name your bucket
   1. Everything else default
   2. Click create bucket



#### Add data&#x20;

If you are adding a few files you can drag and drop _**under 100**_ files at once or you will see this error&#x20;

{% code overflow="wrap" %}
```
You can only upload up to 100 files from the dashboard. Use the Wrangler CLI or API to upload more files.
```
{% endcode %}

What I want to do is add three folders of images, this is for a Trading Card Game&#x20;

1. Folders
   1. Gods - 2000 cards&#x20;
   2. Man - 2000 cards
   3. Demons - 2000 card

Lets see how to upload multiple folder and images.... to be continued&#x20;

Note\*

_**wrangler CLI or API has a limit where i cant push what i need**_

1. rClone is looking like a better way
   1. On Mac&#x20;

{% code overflow="wrap" %}
```
brew install rclone
```
{% endcode %}

2. To config `rclone`

