# Creating a docker image

* 0.0.0.0 - it can access local machine or local host ip address -> This we use while creating flask app
* In project, create Dockerfile
* FROM will pull the baseimage from docker hub
* COPY will copy all the files into app folder in container
* Change the working directory to app
* RUN install dependencies
* CMD run command
* As soon as we run this file, a docker image will get created
* docker build -t <\<docker image name>>  .
* docker images -> To check list of docker images
* docker run -p 5000:5000 <\<docker image>>
* Here 172.17.0.2 is present inside the container, and we cannot access it directly
* We can access it using 127.0.0.1
*

    <figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

```docker
FROM python:3.8-alpine
COPY ./app
WORKDIR /app
RUN pip install -r requirements.txt
CMD
```
