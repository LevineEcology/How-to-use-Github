# How to use Github


This is a basic startup guide for Levine Lab members who are either a) new to Github or b) who need a refresher on basic functions. Github itself has [great documentation](https://docs.github.com/en) if you would like to learn to use more advanced features. 

## 1. Connecting your computer to github with ssh

Github has a [detailed guide](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) to this, though I will go through the basics for mac users (I think a majority of us) just so this is all in one place. 

SSH stands for "Secure SHell," and is a network protocol for securely connecting over an unsecured network. It works through cryptographic elements called "keys", which are unique to your device and must be generated in the command line. If you do remote computing you likely have an ssh key generated on your computer.

### 1.1 Checking for existing keys

1. Open terminal (or your preferred shell program)

2. Enter `ls -al ~/.ssh`

3. Check if the directory lists a public ssh key. Should be something like: "id_rsa.pub". If you already have a key, skip to section 1.4

### 1.2 Generating an ssh key

1. Open terminal

2. Enter `ssh-keygen -t ed25519 -C "your_email@example.com"` , but substitute the email address associated with your github account. 

    The terminal should return: `> Generating public/private ed25519 key pair.`

3. When asked to "Enter a file in which to save a key", press enter.

4. Terminal will ask you to type a secure passphrase, choose something secure and write it down. 

### 1.3 Adding your ssh key to the ssh-agent

1. Open terminal

2. Enter `eval "$(ssh-agent -s)"`

3. If you have macOS Sierra 10.12.2 or later you have to do some extra stuff.

    a. Check if a `~/.ssh/config` file exists by entering `open ~/.ssh/config`
    
    b. If the file doesn't exist, create it by entering: `touch ~/.ssh/config`
    
    c. Open the file by entering `open ~/.ssh/config`. A blank texteditor file should open.
    
    d. Copy the following into the opened file, then save and close the text editor. Note: you can also do this within terminal by typing `nano ~/.ssh/config`.
    
        Host *
            AddKeysToAgent yes
            UseKeychain yes
            IdentityFile ~/.ssh/id_ed25519
            
4. Add your ssh private key to the ssh-agent and store your passphrase in the keychain. To do so enter `ssh-add -K ~/.ssh/id_ed25519`

### 1.4 Add ssh key to your github account

1. Copy ssh public key to your clipboard by entering `pbcopy < ~/.ssh/id_ed25519.pub`

2. On the github website, click on your profile photo in the upper right and click "Settings"

3. In the sidebaar select "SSH and GPG keys"

4. Click "New SSH key"

5. Add a "Title" like "Macbook Pro"

6. Paste your key into the "key field"

7. Click "Add SSH key"


## 2. 


