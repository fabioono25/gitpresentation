# Git Study Notes

The idea is to organize the study of Git, so we have some source for research as needed.

# What's Git

"Sistema de gestão de versão distribuído e sistema de gerenciamento de código fonte, com ênfase em velocidade."

You need create a user [here](https://github.com/).

![](https://github.com/fabioono25/gitstudy/blob/master/git.png)

# Basic Commands:

```sh
$ git init           //initialization of empty git directory
$ git status            
$ git add .          //add files to git repository 
$ git rm arquivo.html -f //remove file from git
$ git commit -m “mensagem do commit”

$ git status -- arquivo.html (consigo resetar o arquivo para a versão anterior, se não tiver feito o git add ainda)

```
![Before run git add command](https://github.com/fabioono25/gitstudy/blob/master/gitStatus2.png)

![After run git add command](https://github.com/fabioono25/gitstudy/blob/master/gitstatus.png)

# Forms of Automatic Authentication:


## Generation a new SSH key and add it to the ssh-agent:

I've had problems with this type of authentication, but is the most recomended one:

https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

```sh
$ 
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]

```sh
sudo apt-get install xclip
xclip -sel clip < ~/.ssh/id_rsa.pub
```

When copy hash key previouly generated, enter in github -> Settings -> SSH and GPG keys, and you must create a new SSH key:

![](https://github.com/fabioono25/gitstudy/blob/master/pasteSSH.PNG)

## Git-credentials

With git-credentials, it's possible create a local file that contains your login and password of github. It maybe incurs in security problems, but is an option:

```sh
git config --global credential.helper store

ls ~/.git-credentials

https://user:password@github.com

```

# Link a local project with repository:

# Merge Commands:

# Working with Tags:

# Rebase vs Merge:

# Using cherry-pick:

# Clean/Reset Project:

# Git-Stash:

# About git-flow

git-flow is a set of extensions that help you improve the git operations.

[Download here.](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

![](https://github.com/fabioono25/gitstudy/blob/master/gitflow.png)



