# Heroku

* Procfile is required 🡪 No extension
  * web gunicorn app:app 🡪 in Heroku this is required for webserver
* runtime.txt
  * python 3.7.10
* First check in local:
  * Create environment
  * pip install -r requirements.txt
  * python app.py
* **Git:**
  * git version 🡪 to check if git is installed
  * cd <\<project path>>
* **Using Heroku Git:**
  * Heroku cli needs to be installed in the system
  * heroku 🡪 this will return the version
  * heroku login 🡪 it will open web browser for login
  * In heroku web browser, go into dashboard
  * Apps 🡪 New 🡪 Create New App
  * Enter App Name, Region
  * Once app is created
  * Select the app
  * Go into deploy
  * Select Git there
  * git init
  * heroku git remote: -a <\<app\_name>>
  * git add .
  * git status
  * git commit -am ‘first commit’
  * git push heroku master
  * Once it is pushed, go to App 🡪 Open App
* **Using Git:**
  * In git, create a repo
  * git init
  * git add README.md
  * git commit -m "first commit"
  * git branch -M main
  * git remote add origin https://github.com/hiteshbwankhede/mlnew.git
  * git push -u origin main
  * if existing repo:
  * git remote add origin https://github.com/hiteshbwankhede/mlnew.git
  * git branch -M main
  * git push -u origin main
  * if password asked when push, then we need to enter token
  * go to github 🡪 Settings 🡪Developer Settings 🡪 Personal Tokens 🡪 Generate token
