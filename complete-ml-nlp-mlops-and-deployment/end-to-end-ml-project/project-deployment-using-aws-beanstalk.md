# Project Deployment using AWS Beanstalk

*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
* Elastic beanstalk is like an instance of linux machine
* For code to reflecrt from git to elastic beanstalk, we will be using code pipeline
* This pipeline is CD pipeline
* Step 1: Create elastic beanstalk instance, environment
* Step 2: Code pipeline
* add a folder .ebextension
* inside it add python.config file
* To be used if not using docker
* We need a application.py file (copy app.py)

```python
option_settings:
  "aws:elasticbeanstalk:container:python":
    WSGIPath: application:application
```

* Login into AWS
* Search elastic beanstalk -> Applications
* Create Application
* Enter Application, Enter Platform - Python 3.8, Application Code - Sample application
* This will create environment also
* Now AWS -> Search -> Code Pipeline
* Create Pipeline
* Enter Pipeline name, Source Provider - Git, Connect to github, Select repo and branch
* Add build stage - optional
* Deploy Provider -> Elastic Beanstalk -> Select Application name
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
* In the application, we can see the URL application
* If we make any changes in code, then we will have to run Release change
