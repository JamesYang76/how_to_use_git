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

##### git add
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
##### git status
``` bash
$ git status
```

##### git rm
To delete files or remove files from tracked status. 
In case of deleting files,\
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
