# Push Docker image to Docker hub

* Log into docker hub
* We can create a private or public repository
* In local, we want to rename the docker image
* Method 1:&#x20;
* docker image rm -f <\<docker image>>
* docker build -t <\<user\_name>>/<\<app\_name>> -> We need to put user name also in docker image name
* Method 2:
* docker tag <\<image\_name>>    <\<user\_name>>/<\<app\_name>>
* docker push <\<app\_name>>:latest
* Latest tag will be shown in docker hub
* This will push docker image to docker hub
* We can download image and run locally also
*
