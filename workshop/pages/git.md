---
title: Git & GitHub 
author: Wyoming IBC
date: October 7, 2019
---

[Return to Main Page](../index.html)

<br><br>


## Table of Contents


[1.1 How does Git work?](#how-does-git-work)

[1.2 Settings up SSH-keys](#setting-up-ssh-keys)

[1.3 Checking your SSH Keys](#checking-your-ssh-keys)

[1.4 A Typical Authentication Session](#a-typical-authentication-session)

[1.5 Notify Your Computer About the Keys](#notify-your-computer-about-the-keys)

[1.6 Add SSH Keys to Your GitHub Profile](#add-ssh-keys-to-your-github-profile)

[1.7 Create a New Repository on GitHub](#create-a-new-repository-on-github)

[1.8 Upload Your Local Repo to GitHub](#upload-your-local-repo-to-github)


<br><br><br>


## What is Git and Why do I need it?

``Git`` is a version control system.  Don't let that make you feel like you are a software engineer.  You don't have to be one for it to be useful to you.  In the simplest terms, ``git`` keeps a journal of all the changes you will make to any files and folders (create, edit, copy, move, delete etc.) in a given project.  Think of it as a virtual assistant that is always listening and keeping track of what you do.  

``GitHub`` as you probably already figured out, is an online resource that allows people to host and archive their code.  The code can be updated/maintained from multiple computers that you may have access to.  You may keep it all to yourself, share it with collaborators or if its useful enough, share it with the community at large.  Code is divided into repositories on GitHub and you may have one or a hundred each dedicated to a different project you are working on.  Consider that you are teaching a course for which you may host the weekly materials such as presentations, assignments and exam solutions to a GitHub repository and then share the repo with your students.  

As you can see, one doesn't really need to be a software programmer for Git and GitHub to be useful to them.  With this introduction, we are barely scratching the surface.  In the Further Reading section below, you will find additional resources to learn about these tools. For now, we will set up your environment so it's usable today.


<br><br>

### 1.1 How does Git work?

- **Note For Windows Users**: Please install git from [https://gitforwindows.org/](https://gitforwindows.org)

- Open the commandline terminal on your system.  For Windows, right click and choose Git Bash.  For Mac, search for ``terminal`` in the spotlight search.


<center>
<img src="git-bash.png" width=300></img>
<img src="terminal.png" width=400></img>
</center> 

- Check whether ``git`` is working on your system:

```bash

git --version

git version 2.20.1 (Apple Git-117)

```
   

- To check git's documentation i.e. help manual

```bash

man git


```


<center>
<img src="githelp.png" width=750></img>
</center>


- To exit the interactive documentation


```bash
q
```


- Check the Status of the current directory where your prompt is located:

```bash
git status

fatal: not a git repository (or any of the parent directories): .git

```

- You haven't created any ``git`` repositories yet on your system, so this warning message is to be expected.

- Let's create a new repository for testing purposes. First, check where you are on the system, then create a new folder named ``gitproject``.


```bash

pwd

/Users/wyoibc

mkdir gitproject

cd gitproject

pwd

/Users/wyoibc/gitproject

``` 


- Initiate a new repository

```bash

git init

Initialized empty Git repository in /Users/wyoibc/gitproject/.git/


```

- Check the status again

```bash
git status

On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

```

- This is normal as well since we haven't yet created any content in here.  Now let's go ahead and create a new file.

```bash

touch README.md

vim README.md

```

- Create some content in the file


```bash

---
title: Learning the Basics of Git
author: Wyoming IBC
date: October 7, 2019
---

This is a new repository.

```

- Save the changes and exit

```vi

:wq

```

- Now check the git status again


```bash

git status


On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use "git add" to track)

```

- As you can see, Git is now aware of the changes you made to this repository.  It knows that there is a new file, although the file is not yet on Git's roll call.  This is by design.  Often times, you don't want every file/folder to be tracked by git.  So git only tracks changes in files when you ask it to.  Let's go ahead and do that.

```bash

git add README.md

git status

On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md

```

- The next logical step here is to ``commit`` this file to git and then push the contents of the repository to your GitHub account.  But before we get there, we need to do a couple of preparations:

<br><br>


### 1.2 Setting up SSH Keys

SSH translates into **S**ecure **SH**ell which allows for encrypted communication over the network between two computers. What are keys then you might ask?  They are secure passwords, usually a very long alphanumeric sequence of characters.  Notice the plural.  Why key**s**?  That's because in the world of encryption, there are two keys:

- A private key (known only to you)
- A public key (that you can share with others) as a token of your identity.

You can use this pair of SSH keys while communicating with remote computing systems so as to identify yourself over an encrypted network.  For example, you an enhance and automate your workflow with the GitHub account through the use of SSH keys.  So how does it work?


- First, create a pair of SSH-keys; use the email address associated with your GitHub account:


```bash

ssh-keygen -t rsa -b 4096 -C "user@email.com"

```

```bash

Generating public/private rsa key pair.

Enter a file in which to save the key (/Users/wyoibc/.ssh/id_rsa): [Press enter]

```

A *private* ssh-key is should be secured with a *passphrase*, which you will be asked to create.  Think of this as a strong password to safeguard your private ssh-key.  Make this passphrase strong and secure, and write it down on a post-it or in your notebook somewhere.


```bash

Enter passphrase :

Enter same passphrase again:

```

<br><br>


### 1.3 Checking Your SSH Keys

Your keys have now been stored in the location you chose above e.g. ``/Users/wyoibc/.ssh``.  Let's go there and check to make sure.

```bash
cd /Users/wyoibc/.ssh/

ls -lh

-rw-------  1 wyoibc  inbre   1.7K Oct 07  2019 id_rsa
-rw-r--r--  1 wyoibc  inbre   406B Oct 07  2019 id_rsa.pub


```

- Key ending in ``.pub`` is your public key which you can share with a remote server.  But what's inside it?


```bash
cat id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA6UJHt+SrbvC2K/E/FozdqrsScVYZmdv476b4A/4takitEXEDjorzXWAHcMHSP/pu3VPlZv6G5s04QkXYRMYxpb3c+LY+7+I39i6aYtGbbkx+HiLIGXDw5R5Pqlh+aSec1ndEXv5aK5yWghMDpOmaq4K+rrhd70zRem28+uUhZeCocJxr56ORIHhBAI84ZKrk2tOnuaD8ad4AKoidM1y9CHRPRB3HzgmaEvO3YzZgiM5A83EkSHpmR1lZnFBvAibX6+lJNYMHwy3fsuxDml1GpDNUCTesSkzQX7L+MBppuylm358vW7xyGdZP245kLYNwqja5nRKprL2uC9rwmQ3T6Q== wyoinbre@gmail.com

```

- What about the private key?

```bash

cat id_rsa

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: DES-EDE3-CBC,4CC25AF5303CA059

---
---
---

-----END RSA PRIVATE KEY-----


```
<br><br>


### 1.4 A Typical Authentication Session


So how do these keys work together allow secure communication with a remote server?  

- The public key is shared with the server you are trying to communicate with.

- When you try to connect to the server, it looks at your public key, and sends a manifest to your computer.  Your computer then checks your public key against the private key and if they match, notifies the server that you are who you say you are.

- Server logs you in or allows file/data transfer.


<br><br>


### 1.5 Notify Your Computer About the Keys

There is an SSH agent on your system which needs to be notified of the presence of ssh keys.  This is a two step process:

- First create a configuration file named ``config``

```bash

cd /Users/wyoibc/.ssh

vim config

```

- Add the following lines to your newly created config file. Pay attention to the upper and lowercase letters.


```bash
Host *
   AddKeysToAgent yes
   UseKeychain yes

Host YOUR_GITHUB_USER_NAME.github.com
        HostName github.com
        User git
        PreferredAuthentications publickey
        IdentityFile /Users/wyoibc/.ssh/id_rsa

```


- Second, notify the ssh agent


```bash

ssh-add -h

ssh-add: illegal option -- h
usage: ssh-add [options] [file ...]
Options:
  -l          List fingerprints of all identities.
  -E hash     Specify hash algorithm used for fingerprints.
  -L          List public key parameters of all identities.
  -k          Load only keys and not certificates.
  -c          Require confirmation to sign using identities
  -m minleft  Maxsign is only changed if less than minleft are left (for XMSS)
  -M maxsign  Maximum number of signatures allowed (for XMSS)
  -t life     Set lifetime (in seconds) when adding identities.
  -d          Delete identity.
  -D          Delete all identities.
  -x          Lock agent.
  -X          Unlock agent.
  -s pkcs11   Add keys from PKCS#11 provider.
  -e pkcs11   Remove keys provided by PKCS#11 provider.
  -q          Be quiet after a successful operation.
  -A          Add all identities stored in your keychain.
  -K          Store passphrases in your keychain.
              With -d, remove passphrases from your keychain.


```

- Check what the ssh agent has in its memory 


```bash

ssh-add -l

The agent has no identities.


```


- Good! Let's add our identity


```bash

ssh-add /Users/wyoibc/.ssh/id_rsa

Enter passphrase for /Users/wyoibc/.ssh/id_rsa: 

Identity added: /Users/wyoibc/.ssh/id_rsa (/Users/wyoibc/.ssh/id_rsa)


```
- Check the memory one more time


```bash

ssh-add -l

2048 SHA256:ZtqsHDh1QDAKDIKzQ4J4FYlnSGi3Di17mlJzakGtxF4 /Users/wyoibc/.ssh/id_rsa (RSA)

```


<br><br>

### 1.6 Add SSH Keys to Your GitHub Profile


- Navigate to [https://github.com/YOUR_USER_NAME](https://github.com/YOUR_USER_NAME)


- Then follow these steps:

<center>
<img src="step1.png" width=800></img>
<img src="step2.png" width=300></img>
<img src="step3.png" width=800></img>
<img src="step4.png" width=800></img>
</center>


Give your key whatever name you'd like, but don't use spaces or special characters in that name.  Then paste the contents of your ``id_rsa.pub`` in the provided box. Then save.  Your saved key should appear like this:


<center>
<img src="step5.png" width=800></img>
</center>


<br><br>

### 1.7 Create a New Repository on GitHub

- Follow on screen instructions for creating a new repo called ``gitproject``

- Make sure **not** to initialize the repo with a README

- Once the repo is generated, use the following procedure for uploading your local work to GitHub


<br><br>

### 1.8 Upload Your Local Repo to GitHub

- First go to the repository where you had created a README.md file

```bash

cd /Users/wyoibc/gitproject

cat README.md

---
title: Learning the Basics of Git
author: Wyoming IBC
date: October 7, 2019
---

This is a new repository.


```

- Check git status

```bash

git status

On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md

```

- Configure git to use your github credentials

```bash

git config user.name "YOUR GITHUB USER NAME" ## Keep the quotes

git config user.email "YOUR EMAIL ASSOCIATED WITH GITHUB"  ## Keep the quotes

```

- Check your settings

```bash

git config --list

user.name=wyoibc

user.email=wyoinbre@gmail.com

```

- Now we are good to upload; First, commit the README.md to git 

```bash

git commit -m "A helpful note about your changes" ## You could say something like "Initial commit"

```

- Tell git your repository's name

```bash

git remote add origin git@github.com:wyoibc/gitproject

```

- Finally push changes

```bash

git push -u origin master

```

- Ideally, you should see something like the following:


```bash

Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 328 bytes | 328.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:wyoibc/gitproject
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```

- This indicates that the repo was successfully synced with GitHub.  Go to GitHub and check it out:

	- [https://github.com/YOUR_GITHUB_USERNAME/gitproject](https://github.com/YOUR_GITHUB_USERNAME/gitproject)


<center>
<img src="step6.png" width=800></img>
</center>

