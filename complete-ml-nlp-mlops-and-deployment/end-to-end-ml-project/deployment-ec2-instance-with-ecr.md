# Deployment EC2 instance with ECR

**Steps:**

1. Docker file
2. Github workflow
3. Create Iam user in EWS - For control access to different developer and admin users
4. Create a repo in ECR
5. Go to EC2 instance and create a virtual server - Select instance name, configuration



* Here we need Dockerfile
* Create a folder .github/workflow
* main.yaml
* In this we will have CD CD pipeline integrated
* It will have 3 jobs - integation, build and push image to ecr repository and deployment
* ECR is for storing, managing and deploy docker images
* We will also have to maintain aws credentials info also
* This can be fetched from github -> actions -> workflow -> deploy to ECS -> This will give us the yaml file
*
*
*
