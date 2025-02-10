# Git

* [https://github.com/Monalsingh/VisionAVI](https://github.com/Monalsingh/VisionAVI)
* [https://github.com/Monalsingh/VisionAVI-Dataset](https://github.com/Monalsingh/VisionAVI-Dataset)
* Based on tasks there will be a branch
* If 3 developers working on a task, then they will use a single branch
* Branch:
  * main/master ⇒ stable code, reviewed, production code
  * branch1 ⇒ changes for task ⇒ push ⇒ review ⇒ pull request&#x20;
  * We create new branch from main
* If there are branch1 and branch2, and branch1 has already been merged with main
* If we try to pull branch2 to main ⇒ It will conflict error
* git status ⇒ shows current branch
* git branch ⇒ to get all the branches
* git pull origin main ⇒ To check if the current branch is upto date with main branch
* git branch <\<name>> ⇒ this is in local, it will not be visible in git
* git checkout <\<branch\_name>> ⇒ switch to the branch
* git status
* git add .
* git commit =m <\<update>>
* git push origin
* This will push the code changes in branch in git
* There we will create pull request ⇒ In description add details about the change
* If we make any changes, then it will be highlighted in vs code
* If we make some changes and then commit, then it will create a checkpoint
* If we add some more lines and get some errors, then we can revert to checkpoint
* git pull ⇒ to pull the code changes from git to local
* After merging its upto us, if we want to keep or delete the branch
