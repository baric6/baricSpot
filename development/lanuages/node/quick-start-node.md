# Quick start node



1. Create Empty folder on desktop
2. Open with VScode and open terminal
3. &#x20;Use the following commands

Create node

```
npm init -y
```

install dependencies

```
npm i express nodemon 
```

4. Make changes to the package.json file. Like if you are using nodemon, add what is missing under the scripts dictionary

```
"scripts": {
 "test": "echo "Error: no test specified" && exit 1"
 "start": "node index.js", 
 "dev": "nodemon index.js",
```

5. Make a file name index.js (this is your main server with node)

```
const express = require('express'); 
const app = express(); 
const port = process.env.PORT || 3000;
app.listen(port, () => {
               console.log(Server running on http://localhost:${port}); 
});
```

6. start node

```
npm run start 
```

or&#x20;

```
npm run dev  
```

