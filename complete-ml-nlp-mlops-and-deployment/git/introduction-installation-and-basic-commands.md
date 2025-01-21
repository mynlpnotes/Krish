# Introduction, Installation and Basic Commands

* [https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)
* Free and open source distributed version control system that's responsible for everything github related that happens locally on computer
* Create a repo on git
* git --version -> To check if git has been installed

**Basic config:**

* git config --global user.name “\[firstname lastname]”
* git config --global user.email “\[valid-email]”
* git config --global color.ui auto



1. **Create a new repository on the command line**

* create/modify a file
* git init  -> Initializes empty git repository
* git add .
* git status -> We can see the untracked files, files in which changes made
* git commit -m 'first commit' -> Pushed to staging, which will be pushed to git
* git branch -> initially it will be on master
* git branch -M main -> It will rename master to main
* git remote add origin <\<git clone url>>
* git push -u origin
* git remote -v -> this will show from where we pull and where we push



* If we made changes to any file, and if we dont want it, then we can use git restore filename -> this will restore it from staging env

2. Push an existing repository from command line

* Navigate to the path where the repo needs to be clonned
* git clone <\<git path>>
* git add .
* git status
* git commit -m "message"
* git push origin

