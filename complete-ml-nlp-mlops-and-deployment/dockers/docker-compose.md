# Docker compose

* Consider a web app which runs in a container&#x20;
* If this web app also wants to user Mysql, redis etc
* So this needs to be run as a separate container
* Then this web app can interact with this containers
* Docker compose is a tool for defining and running multi container docker applications
*

    <figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
* We will create a dockercompose.yml
* Here we will put all the requirements and they will be able to communicate with each other
*

    <figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>
* Create a dockerfile for the web app
* ENV FLASK\_APP = app.py -> Create environment variable
* ENV FLASK\_RUN\_HOST = 0.0.0.0
* EXPOSE -> Specify port number that will be exposed from the container
*

    <figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

docker-compose.yml

*

    <figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>
* docker compose up -> this will run the .yml file
* If any error in any of the services, then we have to delete the containers and then do docker compose
* We can use docker volumes if we dont want this tedious process of re-building again
* docker compose stop -> to stop the containers
