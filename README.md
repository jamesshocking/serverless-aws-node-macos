# serverless-aws-node-macos
Setup instructions for MACOS with Serverless, AWS, Nodejs and Git

## Runtime Dependencies
Install, conda, node, git, serverless

## Step 1: Setup Node
```bash
npm set init.author.name "your name"
npm set init.author.email "your email"
npm set init.author.url "any url that you have"
npm set init.license "MIT"
npm set init.version 1.0.0"
```
## Step 2: Setup Git for SSH
From the terminal window:
```bash
cd ~/.ssh
ssh-keygen -t rsa -C "email address"
```
If the ~/.ssh folder does not exist, create it.  Accept the defaults offered by ssh-keygen.  When complete copy the public key to the clipboard:
```bash
pbcopy < id_rsa.pub
```

## Step 3: Setup a Git for SSH access
- Sign into github and go to /account/ssh.keys
- Create a new ssh key
- Paste in the public key from the clipboard, and assign a name
- Click add key
- Now at the terminal (one-time) add your personal details to git
```bash
git config --global user.name "your name"
git config --global user.email "your email"
```

## Step 4: Create a Git repo

## Step 5: Setup Serverless
- Install Serverless from (https://www.serverless.com/framework/docs/getting-started/)[Serverless Installation Instructions]
- Once installed, at the terminal run:
```bash
serverless plugin install -n serverless-lift
```
- Run serverless at the terminal and follow the prompts.  Serverless will create a folder using the same label that you assign to the project name.
```bash
serverless
```
## Step 6: Setup serverless project for NPM and GIT
- First setup Node
```
cd <project name>
npm install
npx license mit > LICENSE
npx gitignore node
npm covgen <email address> (optional step that creates a document)
npm init -y
```
- Now setup GIT
```bash
git init
git add -A
git commit -m "<message e.g. initial commit>"
git branch -M <branch name - suggest main>
git remote add origin <path to ssh repo taken from Github>
git push -u origin <branch name e.g. main>
```

## Step 7: Using Serverless
To deploy your code to AWS using serverless
```bash
serverless deploy -v
```
To invoke a function in your node project, emulating AWS
```bash
serverless invoke -f <function name> -l
```
To uninstall a project from AWS
```bash
serverless remove
```
## Step 8: To post updates to GIT
```bash
git add -A
git commit -m "<message describing update>"
git push origin <branch e.g. main>
