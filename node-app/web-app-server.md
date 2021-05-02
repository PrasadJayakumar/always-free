# Web App Server
- [Heroku - Free Plan](https://www.heroku.com/pricing)
  - 550-1,000 dyno hours per month
  - Deploy with Git and Docker
  - Custom domains
  - Container orchestration
  - Automatic OS patching
- [Heroku Dashboard](https://dashboard.heroku.com/apps)
- [Heroku Dev Center](https://devcenter.heroku.com/)

## Getting Started

Refer the following articles for detailed instructions
- [The Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
- [Managing Your SSH Keys](https://devcenter.heroku.com/articles/keys)
- [Getting Started with NodeJS](https://devcenter.heroku.com/articles/getting-started-with-nodejs) 

Summary of steps related to Ubuntu desktop is provided below

```sh
# Install Heroku CLI
$ sudo snap install heroku --classic

# Verify installation
heroku --version

# Verify prerequisites
node --version  # Node greater than 10
npm --version
git --version

# Login to your Heroku account
$ heroku login
```

```
# SSH Setup
# Heroku supports RSA and DSA key formats. ECDSA keys are currently not supported.
$ ssh-keygen -t rsa -C your.email@gmail.com
$ heroku keys:add heroku-ssh.pub

# Create an entry in config file
$ vi ~/.ssh/config
Host heroku.com
  HostName heroku.com
  IdentityFile ~/.ssh/heroku-ssh.key
  IdentitiesOnly yes

# Validate the connection
$ ssh -v git@heroku.com
```

```
# Create an app 
$ heroku create always-free

# Create a sample Vue app
$ npm install -g @vue/cli
$ vue --version
$ vue create always-free

# Verify if the Vue app is up and running
$ cd always-free/
$ npm run serve

# Create an express app
$ npm install express --save
$ vi server.js
```
```js
const express = require('express');
const path = require('path');

const app = express();
app.use(express.static('./dist'));
app.get('/*', function (req, res) {
  res.sendFile(path.join(__dirname, '/dist/index.html'));
});

const server = app.listen(process.env.PORT || 8080, () => {
  console.log(`App is running at http://localhost:${server.address().port}`);
});
```
```
$ vi Procfile
web: npm start

$ vi package.json
  "start": "node server.js",

# Create a new git repo
$ git init
$ heroku git:remote -a always-free
# Output: https://git.heroku.com/always-free.git

# Deploy your app
git add .
git commit -am "vue 2 starter code"
git push heroku master
# Output: Build succeeded!
# Output: Verifying deploy... done

# Open the web app and check
# https://always-free.herokuapp.com/
```