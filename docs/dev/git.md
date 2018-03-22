# Version control using Git


## Version control system, what is it ?

-  Manage your code and its evolutions
-  Keep an history to go backwards.

_For what_ : 

Mostly for code, but also for latex and any text file ! 
Not adapted to big data, media files... 

## Git
_Git, a decentralized version control system_ :

-	Decentralized (no need of a server !),
- 	Secure,
-	Fashionable (widely used with a strong community)

For all OS (even Windows !)

## Git, Github, Gitlab, GitKracken etc ...
Before going further, let's clarify some terms that you have heard.
Git is 
Github or Gitlab are web application built around Git to provide collaborative services.
GitKracken, are Graphical interfaces built upon Git to ease its use notably when collaborating with others over a Github/Gitlab platform.


##Git's Workflow

![Git Workflow][workflow]{: style='width: 550px;' }
{: .center }

[workflow]: images/git_workflow.png


## Installation and configuration 

_Installation :_ 
Download [here](http://git-scm.com/downloads/)
and follow instructions.

_Configuration :_

Color is nice !

```sh
git config --global color.diff auto
git config --global color.status auto
git config --global color.branch auto
```

Your credentials (useful for collaborative work).

```sh
git config --global user.name "votre_pseudo"
git config --global user.email moi@email.com
```

## My first project

_Init a repository_

```sh
git init
```

_or copy an existing one)_

```sh
git clone
```


## My first commit

_What's a commit ?_

An atomic update of code, followed by an (explicit !) commentary.
The more you commit the easier it is for you to follow your code !

```sh
git status
git add 
git commit
```


## Sir, I made a mistake !

```sh

git commit --amend
git revert
```


## Handle history

```sh
git log
git diff
git checkout
```

## Branches

_A branch_ :

-  An "alternative" of your code
-  The end of multiple directories !

Create or remove easily branches of your code. 

```sh
git branch

git checkout -b maBranche
```


## Now we add a server...

_For what ?_

Collaboration and backup

_Declare the remote repository_

```sh
git remote add origin ...
```
_Get and send_
```sh
git push
git pull
```

## Merge

```sh
git merge
```

If two persons modify the same line => Conflit !

Don't panic Git tells you everything !


## To go further

```sh
git stash
git tag
.gitgnore
...
man git
```


_References :_

-  [Open Classrooms](http://openclassrooms.com/courses/gerez-vos-codes-source-avec-git)
-  [Miximum](http://www.miximum.fr/enfin-comprendre-git.html)
