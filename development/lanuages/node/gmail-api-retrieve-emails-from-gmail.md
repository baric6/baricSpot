# Gmail API retrieve emails from gmail

#### 1. **Set up Gmail API:**

* Go to the Google Cloud Console.
* Create a new project.
* Go to **APIs & Services > Library**, search for "Gmail API" and enable it.
* Go to **APIs & Services > Credentials**.
  * Create **OAuth 2.0 credentials**.
  * Set up OAuth consent and download the `credentials.json` file.

2\. **Node.js Project:**

```bash
npm init -y
npm install googleapis fs readline
```

```javascript
const fs = require('fs');
const readline = require('readline');
const { google } = require('googleapis');

// Path to the credentials file downloaded from Google Cloud Console
const CREDENTIALS_PATH = 'credentials.json';
const TOKEN_PATH = 'token.json';

// Gmail API scopes
const SCOPES = ['https://www.googleapis.com/auth/gmail.readonly'];

// Load the credentials and authorize the client
fs.readFile(CREDENTIALS_PATH, (err, content) => {
    if (err) return console.error('Error loading client secret file:', err);
    authorize(JSON.parse(content), listEmails);
});

function authorize(credentials, callback) {
    const { client_secret, client_id, redirect_uris } = credentials.installed;
    const oAuth2Client = new google.auth.OAuth2(client_id, client_secret, redirect_uris[0]);

    fs.readFile(TOKEN_PATH, (err, token) => {
        if (err) return getAccessToken(oAuth2Client, callback);
        oAuth2Client.setCredentials(JSON.parse(token));
        callback(oAuth2Client);
    });
}

function getAccessToken(oAuth2Client, callback) {
    const authUrl = oAuth2Client.generateAuthUrl({
        access_type: 'offline',
        scope: SCOPES,
    });
    console.log('Authorize this app by visiting this url:', authUrl);
    const rl = readline.createInterface({
        input: process.stdin,
        output: process.stdout,
    });
    rl.question('Enter the code from that page here: ', (code) => {
        rl.close();
        oAuth2Client.getToken(code, (err, token) => {
            if (err) return console.error('Error retrieving access token', err);
            oAuth2Client.setCredentials(token);
            fs.writeFile(TOKEN_PATH, JSON.stringify(token), (err) => {
                if (err) return console.error(err);
                console.log('Token stored to', TOKEN_PATH);
            });
            callback(oAuth2Client);
        });
    });
}

function listEmails(auth) {
    const gmail = google.gmail({ version: 'v1', auth });
    
    const senderName = 'example';  // Name to search for
    const subjectKeyword = 'project';  // Word in the subject line to search for

    gmail.users.messages.list({
        userId: 'me',
        q: `from:${senderName} subject:${subjectKeyword}`,  // Search emails from a specific sender and subject keyword
        maxResults: 10,  // Number of emails to fetch
    }, (err, res) => {
        if (err) return console.error('The API returned an error: ' + err);
        const messages = res.data.messages;
        if (!messages || messages.length === 0) {
            console.log('No messages found.');
            return;
        }
        messages.forEach((message) => {
            gmail.users.messages.get({
                userId: 'me',
                id: message.id,
            }, (err, res) => {
                if (err) return console.error('Error retrieving message:', err);

                // Extract subject
                const subject = res.data.payload.headers.find(header => header.name === 'Subject').value;

                // Extract the full body of the email
                let emailBody = '';
                const parts = res.data.payload.parts;
                if (parts && parts.length > 0) {
                    parts.forEach((part) => {
                        if (part.mimeType === 'text/plain') {
                            emailBody += Buffer.from(part.body.data, 'base64').toString('utf-8');
                        }
                    });
                } else if (res.data.payload.body.data) {
                    emailBody = Buffer.from(res.data.payload.body.data, 'base64').toString('utf-8');
                }

                // Save the full email (subject + body)
                const emailData = `Email ID: ${res.data.id}\nSubject: ${subject}\nBody:\n${emailBody}\n\n---\n\n`;
                saveEmailToFile(emailData);
            });
        });
    });
}

function saveEmailToFile(data) {
    fs.appendFile('emails.txt', data, (err) => {
        if (err) return console.error('Error saving email:', err);
        console.log('Email saved!');
    });
}


function saveEmailToFile(data) {
    fs.appendFile('emails.txt', data, (err) => {
        if (err) return console.error('Error saving email:', err);
        console.log('Email saved!');
    });
}

```

Example Output:

```sh
Email ID: 17c4b64f43f0b17a
Subject: Project Alpha - Meeting Notes
Body:
Hi Team,

Here are the meeting notes for the Project Alpha discussion held last week. Please review and send any feedback by Friday.

Best regards,
John

---

Email ID: 1794b50d2c88b11f
Subject: Re: Project Alpha - Follow-up
Body:
Thanks for the update, Sarah. I'll follow up with the team on the next steps for Project Alpha. 

Let's aim to finalize the timeline next week.

Best,
John

---

Email ID: 160f74f1c2d3e6a1
Subject: Project Alpha Launch Plan
Body:
We have finalized the launch plan for Project Alpha. The timeline is set for next month. Let’s make sure the team is ready for the deadlines.

Thanks,
The Team
---


```
