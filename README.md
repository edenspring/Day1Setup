# Day 1 Setup Guide
Today we’ll take students through setting up their environments to succeed here at a/A. You can reference the unified setup to get an idea of what to do, however this document will provide an outline for what needs to be done.

## Node/NVM
* Students will run the install script from NVM’s GitHub repository:
* Current as of 10/24/2022
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash`
* Once the script finishes, students will close and restart their terminals
* When the terminal comes back up, students will run
`nvm install 16`
* Once that finishes, they’ll run
`npm install -g mocha`
* Confirm Node is found in the correct place by running 
`which node`
* You should get output along the lines of
`/home/userName/.nvm/versions/node/v16.xx.x/bin/node`
* This will make sure their environment is using the version fron NVM rather than whatever binaries their system came with

## VSCode
* download VSCode for the appropriate OS 
* https://code.visualstudio.com/
### WSL Users Need Remote Extension
* Looks like its no longer called remote, but instead WSL
* it has the Linux penguin as its icon
* VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl
### Check to make sure `code .` works
* Self explanatory, try `code .` from terminal
* Mac users may need to add it to path. Manually open VSCode, hit cmd shift p, search for path, select the option to add VSCode to path

## GitHub
* Students will need to setup GitHub Auth
* They have some choice here, but I encourage PAT as its a bit easier than SSH setup
* I wrote [this guide](https://hackmd.io/@AgDXdHgSSPKsJIhCxlaTuA/BJtNu88fF) a while back if they want to use SSH
* If they choose to do SSH, let em go on their own.
### PAT setup
* Have students head over to https://github.com/settings/tokens and click Generate new token (classic)
* Tokens are environment specific, make sure they give the token a note so they know which computer this is for
* Next, change expiration to No expiration
* The only scope they really need is Repo, make sure all boxes are checked
* Then scroll to the bottom and click Generate token
* This will take them to a new page that shows them their token. MAKE SURE THEY SAVE IT SOMEWHERE! Put it in a text file, something. At least keep the page open
* Turn their attention to their terminals
### Local steps for everyone
* Have them run `git config --global user.email their@ema.il` filling in the email they address the use for GitHub
* Next have them run `git config --global user.name "First Last"` where First Last is their (you guessed it) first and last names
* Finally, if they are using a PAT, have them run `git config --global credential.helper store`
* Next have them make a new directory `mkdir gitHubTest`
* Navigate into the directory with `cd gitHubTest`
* Initialize a new repository with `git init`
* Create a new file with `touch test.js`
* Add the file to the staging area `git add test.js`
* Commit the changes `git commit -m add test"
* Make sure no students run into issues, if they didn't do a global configuration for their email and name it will yell at them
* Once they have committed, have them head over to https://github.com/new
### Creating a remote repository for testing
* make sure they do not use a template
* have them make a new repo, does not matter what they call it but how about gitHubTest
* make sure they set the owner to themselves
* ensure the repository is set to private
* click Create repository
### Linking local and remote
* You should be seeing a page with some code about linking up a local repo to your remote repository
* under the …or push an existing repository from the command line section, have them copy all of the code there. it should look something like
```
git remote add origin https://github.com/edenspring/gitHubTest.git
git branch -M main
git push -u origin main
```
* have them paste that into their terminal where they created their local repo
* once they execute the push command, it will ask for their username
* BEFORE THEY DO THAT, they should find where they have their PAT and copy it to their clipboard
* now enter user name
* on the next screen, it will ask for their password. it does not want their password, it wants their PAT
* paste in the PAT (right click to paste for Windows users). It will not look like it pasted, but it probably did
* hit enter after pasting, should get screens indicating success
* if it did not succeed, they failed at pasting their token. they should try again. if it fails a second time, read terminal output for clues

### Check for WSL2
* Make sure that WSL users are using WSL2. If they aren't, it could be a painful process to upgrade them.
* Make a note of it if they are not on WSL2 and ask a more experienced instructor for help
