# Docker basic commands

* This will pull image from docker hub and run as a container on our machine
* docker pull docker/getting-started -> To pull from docker hub
* docker images -> to get the list of docker images
* We can see the same in docker desktop as well
* docker run -d -p 80:80 docker/getting-started -> To run the application
* \-d -> means detached mode -> it will run independently
* \-p -> assigning port&#x20;
* 80:80 -> assigning host port as 80, and it will communicate with port 80 of the application
* docker ps -> To verify it docker container is running
* 127.0.0.0:80 -> To run the application
* docker stop <\<container id>> -> to stop the container
* We can see this in docker desktop -> containers
* docker image rm -f <\<image id>> -> to remove the docker image
* We can also pull by tag -> docker pull redis:bullseye
* We can run any number of containers on the same port but our host port will be different



*
