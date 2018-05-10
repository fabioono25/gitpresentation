## Git Study Notes

The idea is to organize the study of Git, so we have some source for research as needed.

## What's Git

"Sistema de gestão de versão distribuído e sistema de gerenciamento de código fonte, com ênfase em velocidade."

You need create a user [here](https://github.com/).

![](https://github.com/fabioono25/gitstudy/blob/master/git.png)

## Basic Commands:

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

## Forms of Automatic Authentication:


### Generation a new SSH key and add it to the ssh-agent:

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

### Git-credentials

With git-credentials, it's possible create a local file that contains your login and password of github. It maybe incurs in security problems, but is an option:

```sh
git config --global credential.helper store

ls ~/.git-credentials

https://user:password@github.com

```

## Link a local project with repository:

```sh
git remote -v  //verificar se existe git configurado

git remote add origin https://github.com/fabioono25/gitstudy.git

git push --set-upstream origin master

git clone https://github.com/fabioono25/gitstudy.git
```

## Merge Commands:

Git fetch: atualizar o indicador de cada branch, sem que atualize em si a branch.

Git pull: faz o fetch e o merge (2 comandos).

![](https://github.com/fabioono25/gitstudy/blob/master/merge1.PNG)

![](https://github.com/fabioono25/gitstudy/blob/master/merge2.PNG)

```sh
git merge origin master

git merge

git branch

git log: Q to finish

Reset: utilizar hash para retornar para a versão

```
## Logs:

![](https://github.com/fabioono25/gitstudy/blob/master/logs.PNG)

## Working with Tags:

```sh
git tag version //define tag
git push --tags //upload tag by command line
```
![](https://github.com/fabioono25/gitstudy/blob/master/tag1.PNG)


![](https://github.com/fabioono25/gitstudy/blob/master/tag2.PNG)


![](https://github.com/fabioono25/gitstudy/blob/master/tag3.PNG)


![](https://github.com/fabioono25/gitstudy/blob/master/tag4.PNG)


![](https://github.com/fabioono25/gitstudy/blob/master/tag5.PNG)

## Working with Branches:

Use one branch per feature.

```
git branch feature/atualizacao_template
git branch -D feature/nome_branch

git checkout feature/nome_branch
git checkout master

git branch (visualizar a branch atual)

```

![](https://github.com/fabioono25/gitstudy/blob/master/branch1.PNG)

![](https://github.com/fabioono25/gitstudy/blob/master/branch2.PNG)

![](https://github.com/fabioono25/gitstudy/blob/master/branch3.PNG)

## Merge x Rebase:

### Merge

Sempre partir de onde vc está, e quer saber o resultado final.

![](https://github.com/fabioono25/gitstudy/blob/master/merge1_1.PNG)

Mesma quantidade de commits.
Ideal é remover a branch, pois já está na master.

Git branch -D feature/nome_feature

Git checkout -b feature/nova_branch (crio a branch e dou checkout para ela)

### Rebase:

Conflict Situation:

![](https://github.com/fabioono25/gitstudy/blob/master/rebase1.PNG)


Solução 1: Merge (da master dentro da branch B) - problemas nos logs dos commits - difícil tracking
Merge é manutenção, não faz parte do meu trabalho de manutenção

![](https://github.com/fabioono25/gitstudy/blob/master/rebase2.PNG)

Solução 2: Rebase (atualizando o momento que este corte foi feito) - a idéia é que cada branch reflita o momento que foi atualizada

![](https://github.com/fabioono25/gitstudy/blob/master/rebase3.PNG)

![](https://github.com/fabioono25/gitstudy/blob/master/rebase4.PNG)

![](https://github.com/fabioono25/gitstudy/blob/master/rebase5.PNG)


## Using cherry-pick:


![](https://github.com/fabioono25/gitstudy/blob/master/cherry2.PNG)


Pick the hash
![](https://github.com/fabioono25/gitstudy/blob/master/cherry1.PNG)

Use hash
```
$ git cherry-pick e43a6fd3e94888d76779ad79fb568ed180e5fcdf
```

## Clean/Reset Project:

```
git reset hash //apaga logs commits, mas mantem os arquivos
git checkout -- .
git clean -f //cuidado
git push -f

git reset HEAD~2 //erase 2 logs behind

```

## Git-Stash:

Guarda estados dos arquivos, reverte a branch para algo compatível com a cabeça da branch

```
git add .
git stash //o arquivo que eu criei ficou na stash

git stash list

git stash pop (retorna o que foi colocado na pilha).

```

## Pull Request:

Pedido de inserção de determinada branch dentro da branch master

0 | 1 # quantos commits a branch master possui a mais que esta branch.

![](https://github.com/fabioono25/gitstudy/blob/master/pullRequest1.png)

Reviewers: pedido para alguém revisar o código.

Squash: reunir diversos commits em um só.

Webhooks: Webhooks allow external services to be notified when certain events happen. When the specified events happen, we’ll send a POST request to each of the URLs you provide. Learn more in our Webhooks Guide.   

## Git-Flow:

git-flow is a set of extensions that help you improve the git operations.

```
apt-get install git-flow

git flow init
```

[View here.](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

![](https://github.com/fabioono25/gitstudy/blob/master/gitflow.png)

![](https://github.com/fabioono25/gitstudy/blob/master/nvie-git-workflow-commands.png)


![](https://github.com/fabioono25/gitstudy/blob/master/gitFlow1.png)

![](https://github.com/fabioono25/gitstudy/blob/master/gitFlow2.png)

![](https://github.com/fabioono25/gitstudy/blob/master/gitFlow3.png)

![](https://github.com/fabioono25/gitstudy/blob/master/gitFlow4.png)

![](https://github.com/fabioono25/gitstudy/blob/master/gitflow5.png)


## Criando Arquivo Alias:

```
vi ~/.bashrc

alias gs = ‘git status’
alias gfp = ‘git fetch --prune’
gffp teste_alias

```
![](https://github.com/fabioono25/gitstudy/blob/master/gitalias.png)

## .gitignore:

Examplo:

*.java
temporario*

É possível colocar RegExp.

## Helpfull links

https://github.com/git-tips/tips

https://git-scm.com/book/pt-br/v1/Primeiros-passos

https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html

## Questions and Answers

