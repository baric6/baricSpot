# Quick start node



1. Create Empty folder on desktop
2. Open with VScode and open terminal
3. &#x20;Use the following commands

Create node

`npm init -y`

install dependencies

`npm i express nodemon`&#x20;

4. Make changes to the package.json file. Like if you are using nodemon, add what is missing under the scripts dictionary

"scripts": {

&#x20;"test": "echo "Error: no test specified" && exit 1"

"start": "node index.js",&#x20;

"dev": "nodemon index.js",

4. Make a file name index.js (this is your main server with node)

const express = require('express');&#x20;

const app = express();&#x20;

const port = process.env.PORT || 3000;

app.listen(port, () => {

&#x20;              console.log(`Server running on http://localhost:${port}`);&#x20;

});

5. start node

npm run start&#x20;

or&#x20;

npm run dev
