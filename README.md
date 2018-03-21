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
#### Git clone or init
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


### Git status
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

### Git Branch

##### git branch
To show branch
``` bash
# local
$ git branch
# -a : all, -r : remote
# git branch -a
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