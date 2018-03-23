## Install Git on Mac
First, check xcode package already installed
``` bash
$ xcode-select -p
/Library/Develper/CommandLineTools
```
If there is no xcode, just type `$ git` or `xcode-select --install`
### Git Bash
To use git bash on mac
https://github.com/fabriziocucci/git-bash-for-mac


## Git Config
Here are basic configs for git
``` bash
$ git config --global user.email “jamesyang40k@gmail.com”
$ git config --global user.name “James Yang”
#for atom, atom > install shell commands in atom editor
$ git config --global core.editor "atom --wait"
#for sublime
$ git config --global core.editor "subl -w"
$ git config --global mergetool.sublime.cmd "subl -w \$MERGED"
$ git config --global mergetool.sublime.trustExitCode false
$ git config --global merge.tool sublime
$ git mergetool -y
# change default directory
$ git config --global core.excludesfile ~/.gitignore
$ echo .DS_Store >> ~/.gitignore
``` 
These options can be checked in `$ git config --list` or\
a config file `~/.gitconfig` and `~/.gitignore_global`

For SSH settings,\
https://help.github.com/articles/connecting-to-github-with-ssh/

For local .gitignore,\ 
go to repository and make `.gitignore` and\
fill out the file via https://www.gitignore.io

## Usage
#### git clone or init
If there is a remote repository,
```bash
# ssh
$ git clone git@github.com:JamesYang76/not_hello_world.git
# https
$ git clone https://github.com/JamesYang76/not_hello_world.git

```
If there is no remote repository,
``` bash
$ git init
```  
There will be `.git` directory which was made.


### git status
If there is a new file or modified file, the status is unstaged,\
via `git add`, the file can become staged.\
After the file in staged, it'll be committed through `git commit`\
Also, there are tracked and untracked files. 
untracted files can be tracked via `git add`. For example, a file which is newly made is untracked.\
files in clone are tracked, but unmodified.

##### git add files
Make untracked files or modified files into staged status.
```bash
$ git add .
$ git add git-*.sh
$ git add Documentation/\*.txt
```
##### git commit
Make a version, in other word, make a index for files in only staged.
```bash
$ git commit -m "First Commit"
# add and commit togather
$ git commit -am "First Commit"
```
To change commit message,
``` bash
$ git commit --amend
```
To overwrite last commit,
``` bash
$ git commit -m 'last commit'
$ git add forgotten_file
$ git commit --amend
```

##### git status
``` bash
$ git status
```
##### git mv old_filename new_filename
To rename a file,
``` bash
$ git mv old_filename new_filename
$ git commit -m "Rename file"

```
##### git rm files
To delete files or remove files from tracked status. 
In case of deleting files,
``` bash
$ rm a.txt

$ git rm a.txt
# for several files
$ git rm log/\*.log
# delete all files end of which is ~ 
$ git rm \*~  

$ git commit -m "delete"
```
In case of remove files from tracked status.
``` bash
$ git rm --cached a.log
```
#### git clean -f
To remove untracked files
``` bash
$ git clean -f
# also delete directory
$ git clean -fd

```


### Git Branch

##### git branch
To show branch
``` bash
# local
$ git branch
# -a : all, -r : remote
$ git branch -a
# -v :last commit on each branch
$ git branch -v
```

##### git branch/checkout branch_name
To make a new branch and go to the branch
``` bash
$ git branch testing
$ git checkout testing
```

##### git checkout -b branch_name
To make a new branch and go to the branch in one command
``` bash
$ git checkout -b testing
```

#### git push origin branch_name
To apply branch to remote repository
```bash
$ git push origin testing
```

#### git branch -d branch_name
``` bash
$ git branch -d testing
```

#### git push origin :branch_name
To remove remote branch
``` bash
$ git push origin :testing
#another way
$ git push origin -d testing
```

#### git branch -m old_name new_name
To change branch name
```bash
$ git branch -m old_name new_name
$ git push origin :old_name
$ git push origin new_name
``` 

#### git merge branch_name
To merge testing into master
```bash
$ git checkout master
$ git merge testing
```
To relove merge conflict, open conflicted files and fix them 
```
$ git add file_names
$ git commit -m "resolve merge conflict"
```
#### git rebase base_branch_name
To base branch
```bash
$ git rebase base_branch_name
# if there is conflict, resolve it
$ git add conflicted_files
$ git rebase --continue

```


### show differnces
#### git log
``` bash
#default log
$ git log
#with number : show only the given number recent commit 
$ git log -1
$ git log --branches --oneline --decorate --graph

``` 
#### git log branch_name..other_branch_name
To show difference
```bash
# show there are someting only testing 
$ git -p log master..testing
```

#### git diff
```bash
# show unstaged modification
$ git diff
# show difference between last commit and modification
$ git diff HEAD
# compare previous commit
$ git diff HEAD HEAD^ 
$ git diff commit_id other_commit_id
$ git diff branch_name other_branch_name
```

### Recovery
#### git stash
To stash current status which is unstaged before changing branch.
```bash
# show stashs
$ git stash list
$ git stash
# resotre saved status
$ git stash apply
$ git stash apply stash@{0}
# to apply and remove stash list
$ git stash pop
# remove stash
$ git stash drop
$ git stash drop stash@{0}
# remove all stashs
$ git stash clear
```

#### git revert commited_id
To go back to past, by making new commit
``` bash
$ git revert commited_id
# go back 2 step back from last commit
$ git revert HEAD^
```
#### git checkout commited_id
```
# go back 1 step from last commit
$ git checkout HEAD^
```
#### git checkout HEAD --file_name
Same result with git reset --hard HEAD except only applying a file
``` bash
$ git checkout HEAD --file_name
```


#### git reset --hard HEAD
To go back to lastest commit
``` bash
$ git reset --hard HEAD
```
#### git reset --hard ORIG_HEAD
ORIG_HEAD is previous stage of HEAD
it is used to go back after reset, pull, merge or other actions.
``` bash
$ git reset --hard ORIG_HEAD
```


#### git reset --merge
To cancel a conflicting merge
``` bash
$ git reset --merge
```

### How to syn with remote
#### git remote origin remote_address
To connect my local repository to remote repository
``` bash
$ git remote add origin git@github.com:JamesYang76/not_hello_world.git
#show remote repository
$ git remote -v
``` 

#### git push
To apply local to remote
```bash
$ git push remote_name banch_name
# applly all local branches to remote
$ git push remote_name --all

```

#### git fetch
To syn with remote
``` bash
$ git fetch origin master
$ git merge origin/master
```

#### git push
same result with fetch and merge
```
$ git pull origin master
```

#### when pull request conflict
To pull req testing into master

```bash
$ git checkout master
$ git pull
$ git checkout testing
$ git merge master
#after resolve conflict files
$ git commit -am "resolve"
$ git push origin testing
```

### Tagging
To tag specific points in history as being important,
#### git tag
list available tags
```bash
$ git tag
$ git tag -l "v1.8.5*"
```

#### git tag version -m "message"
To create tag
```bash
$ git tag v1.4 -m "my version 1.4"
$ git tag v1.0 master
$ git tag v1.0 commit_id
```
#### git push origin tag_name
To apply for remote repo
```bash
$ git push origin v0.1
$ git push origin --tags
```

#### git tag -d tag_name
To delete tag
```bash
$ git tag -d v0.1
#remote delete
$ git push origin :refs/tags/v0.1
```
#### git checkout tag_name

## Reference
Git quick reference\
https://education.github.com/git-cheat-sheet-education.pdf\
https://git-scm.com/book/en/v2\
https://guides.github.com/\

For Sotfware Version\
https://semver.org

Git Branch Strategy\
http://nvie.com/posts/a-successful-git-branching-model/\



