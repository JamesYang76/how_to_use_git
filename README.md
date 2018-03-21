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