# Deployment in AWS

* Deployment in elastic beanstalk
* Elastic beanstalk is just like a linux machine, where we can run the application
* We have to create a mechanism to push code from Git to AWS
* This will be done using Code pipeline
* Whenever we make changes in git, we can automatically deploy on AWS on click of a button
* We have to create a folder .ebextension in project
* Inside this we will create a python.config file
* option\_settings:

&#x20;              "aws:elasticbeanstalk:container:python"

&#x20;                          WSGIPath: application: application -> application.py is our app file

* AWS Console -> Elastic beanstalk
* Application -> Create a new application -> In platform -> Select python -> select python version -> Application code -> Sample code&#x20;
* Application will get created
* New environment will get created
* AWS Console -> Search code pipeline&#x20;
* Enter pipeline name -> Enter code source as Git -> Connect to git -> select repo -> select branch -> Enter application name -> Save
* Once the pipeline runs -> Go to application -> Application URL
*



*
