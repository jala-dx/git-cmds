#### How to do git stash.

Run "git log" and pick the one of the hash
git rebase -i <hash>
Retain "Pick" you want to keep
Mark "f" to purge the following commits
git push origin +master


#### How to do multiple PR
1. git clone <repo> - by default this will be your master branch
2. Create a new branch- "git checkout br2" - br2 is my new branch name
3. do your work. commit, "git commit -m 'comments'"
4. Push - git push origin/br2
5. To go back to master branch, do "git checkout master"
6. From master, to go back to br2, run "git checkout br2"


#### How to Pull a PR that is not merged into your local WS

Locate the section for your github remote in the `.git/config` file. It looks like this:

```
[remote "origin"]
	fetch = +refs/heads/*:refs/remotes/origin/*
	url = git@github.com:joyent/node.git
```

Now add the line `fetch = +refs/pull/*/head:refs/remotes/origin/pr/*` to this section. Obviously, change the github url to match your project's URL. It ends up looking like this:

```
[remote "origin"]
	fetch = +refs/heads/*:refs/remotes/origin/*
	url = git@github.com:joyent/node.git
	fetch = +refs/pull/*/head:refs/remotes/origin/pr/*
```

Now fetch all the pull requests:

```
$ git fetch origin
From github.com:joyent/node
 * [new ref]         refs/pull/1000/head -> origin/pr/1000
 * [new ref]         refs/pull/1002/head -> origin/pr/1002
 * [new ref]         refs/pull/1004/head -> origin/pr/1004
 * [new ref]         refs/pull/1009/head -> origin/pr/1009
...
```

To check out a particular pull request:

```
$ git checkout pr/999
Branch pr/999 set up to track remote branch pr/999 from origin.
Switched to a new branch 'pr/999'
```


#### How to add remote upstream
```
git clone https://cto-github.cisco.com/jganapat/learn-go.git

git remote -v
git remote add upstream https://cto-github.cisco.com/atom-hacks/learn-go.git
git remote -v
git fetch upstream
git status
git rebase upstream/master

if you hit merge conflicts
git reset --hard upstream/master


g st
g commit -s -m "comments.."
git add
g push origin master

```


```
814  rm -rf atomix
  815  git clone https://cto-github.cisco.com/jganapat/atomix.git
  816  cd atomix
  817  git remote add upstream https://cto-github.cisco.com/atom/atomix.git
  818  git log
  819  git fetch upstream
  820  git branch
  821  git checkout master
  822  git merge upstream/master
  823  vi releases/apic-v1.txt 
  824  git log
  825  git reset --hard upstream/master
  826  git log
  827  git push origin +master
  828  git log
  829  vi releases/apic-v1.txt 
  830  git status -uno
  831  git add releases/apic-v1.txt 
  832  git commit -s -m 'enable elastic auto-start after boot'
  833  git log
  834  git push origin +master
  835  git log


```
