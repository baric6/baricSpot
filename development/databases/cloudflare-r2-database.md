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

`Note***`` `_**`wrangler CLI or API has a limit where I cant push what I need. It only will proccess a file at a time, I need many files at once`**_

#### Install rClone

rClone is looking like a better way

1. On Mac&#x20;

{% code overflow="wrap" %}
```
brew install rclone
```
{% endcode %}

#### Config rClone

Alot of tutorials tell you to use `rclone config` to let you setup the config via terminal. It was ok but i got confused so i looked for another route. There is a way to write to the config manually via `nano`

1. find where the config file is located on your system
   1. `rclone config file` , should show the path&#x20;
      1. `/Users/<YOUR USER>/.config/rclone/rclone.conf` windows may be different
2. `nano` into that file location, you should see&#x20;

{% code overflow="wrap" %}
```
[r2]
type = s3
provider = Cloudflare
```
{% endcode %}

3. you need to paste under provider

{% code overflow="wrap" %}
```
access_key_id = YOUR_R2_ACCESS_KEY
secret_access_key = YOUR_R2_SECRET_KEY
endpoint = https://<ACCOUNT_ID>.r2.cloudflarestorage.com
acl = private
```
{% endcode %}

4. To find this info&#x20;
   1. On the Left menu bar under: Storage & Databases > R2 Object Storage > Overview. This is where you should see your databases that you created and you can get to the API keys
   2. Towards the bottom of the page under "Account Details" you should see "API Tokens" and a manage button next to it click it.
   3. Create a new User API Token name it and select permissions&#x20;
      1. For testing you can set permissions to `Admin: Read and Write`, all other options are default. _**Make sure you change this to what is needed before sending it out to production**_
      2. When making this API this will be the only time you can view Access key or Secret key. Save it some where if you forget you will have to make a new one
      3. You can change the APIs permissions without making a new API
5. To test your connection to the DB
   1. Make sure to add the colon to the command or it will look for a local file

{% code overflow="wrap" %}
```
rclone lsd r2:
```
{% endcode %}

6. If you get a list of your R2 bucket that you created it worked

{% code overflow="wrap" %}
```
-1 2026-07-05 21:55:27        -1 backup-cards
-1 2026-06-17 17:29:58        -1 cards
```
{% endcode %}

#### Pushing files the the R2

To be continued ...........&#x20;
