---
layout: default
---

# Git HowTo

There are some excellent gui for git like [Sourcetree](https://www.sourcetreeapp.com) and [Github Desktop](https://desktop.github.com) which work on Mac/Windows. There are programs for Linux also but I do not have experience with them.

## Setup ssh keys

It is recommended to use git via ssh instead of https. To save yourself the trouble of entering your password everytime, copy your ssh public key into your git account. The public key is in `$HOME/.ssh/id_rsa.pub` file; if you dont have it, then generate it by typing this in terminal

```shell
ssh-keygen
```

and press enter to all the questions.  Now log in to your git account in your browser, go to settings page where you will find a place to copy the ssh key.

## Watch repositories

When you are collaborating with me on some project, we have to share code via git. When I update the code in my repository, you must get a notification that there is an update. For this to happen, you must watch the repository.

* Github: Go to the webpage of the repository and look for "Watch" link and enable "All activity".
* Bitbucket: Go to the webpage of the repository, click on three dots at the top right of the page, then click on "Manage notifications" and enable watching. Enable notifications for "Commits" and maybe also for "Issues".

## Some rules to follow

1. Before a commit or when creating a pull request, check every changed line and ensure that you made the change and that you would like to check it in.
1. Do not commit trivial changes like adding extra blank line or blank space.  
1. Make sure that files you add don't have execute permission.

## Better diff highlighting

```shell
git diff --word-diff filename
git diff --color-words filename
```

## Adding files

To add all modified files which are already tracked

```shell
git add -u
```

## Undoing commit which is not yet pushed

Suppose you have not pushed your commit to remote. Then undo last commit while keeping changes from it (unstaged)

```shell
git reset HEAD^
```

An equivalent command is

```shell
git reset --soft HEAD~1
```

If you want to undo last commit and throw away the changes

```shell
git reset --hard HEAD~1
```


## Merge previous commits into one

If we want to merge last 6 commits into a single one

```shell
git reset --soft HEAD~6
git commit               # add message
git push --force         # force needed if commit is already pushed to remote
```

## Cleaning up

To remove all untracked files in the current directory

```shell
git clean . -fx
```

To remove all untracked files and directories in the current directory

```shell
git clean . -fxd
```

## Checkout old version

If you want to use an old version of the code, then find the SHA checksum of the commit using `git log` and then do

```shell
git checkout <checksum>
```

The HEAD is now set to the selected commit and you can see this by doing `git branch`. If you now want to go back to master, do

```shell
git checkout master
```

## Making a branch

Create a new branch

```shell
git branch my_branch
```

Checkout your new branch

```shell
git checkout my_branch
```

Make changes in this branch, add files and commit them to your branch. Then push them to remote

```shell
git push origin my_branch
```

To merge your branch into master

```shell
git checkout master
git merge my_branch
```

You can now push master to your origin and then create a pull request.

## Make your fork track original upstream repo

```shell
git checkout master
git remote add upstream git@github.com:upstreamname/projectname.git
```

Now you can get updates from upstream

```shell
git fetch upstream
git merge upstream/master
```

To send these changes to your own remote

```shell
git push origin master
```

## Rebase branch to master

```shell
git checkout master 
git pull origin master
git pull upstream master
git checkout my_branch
git rebase master
```

The last step might indicate some conflicts which have to be resolved.

## Sync branch to master

If your master has changed, you can update your branch. You may also want to squash several commits into one before creating a pull request.

1. `git checkout master`
1. `git pull origin master`
1. `git pull upstream master`
1. `git checkout yourbranchname`
1. `git rebase -i master`
1. A file in an editor program will be automatically open.
1. Change all commits from "pick" to "fixup" but one commit must have "pick"!
1. Save the file and close the editor.
1. `git push -f origin yourbranchname`

## Delete branch which is not merged

```shell
git branch -D my_branch
git push origin :my_branch
```

## Accepting and merging a pull request

```shell
git checkout master
git remote add contributor git://github.com/contributor/projectname
git fetch contributor
git merge contributor/newfeature
git push origin master
```

## Download private repo via ssh

```shell
git archive --remote=ssh://git@bitbucket.org/USERNAME/REPO.git --format=zip \
    --output="FILENAME.zip" master
```

## Create archive locally (without .git)

```shell
cd DIRECTORY
git archive -o latest.zip HEAD
```

## Find hash for your local version of code

```shell
git describe --abbrev=16 --dirty --always
```

## Get a pull request for testing purpose

To test the commits in a pull request, you can fetch the pull, create a branch and then test it.

```shell
git fetch origin pull/9874/head:9874
git checkout 9874
```

## git+ssh over https

On some servers ssh may not be allowed but https is allowed. In this case we can use git+ssh over https by adding following lines to your `~/.ssh/config` file.

```text
Host github.com
   HostName ssh.github.com
   Port 443
Host bitbucket.org
   HostName altssh.bitbucket.org
   Port 443
Host gitlab.com
   HostName altssh.gitlab.com
   Port 443
```

## git config file

```text
[user]
   name = Praveen C
   email = praveen@gmail.com
[alias]
   co = checkout
   cm = commit
   br = branch
[color]
   diff = auto
   status = auto
   branch = auto
   interactive = auto
   ui = true
   pager = true
```
