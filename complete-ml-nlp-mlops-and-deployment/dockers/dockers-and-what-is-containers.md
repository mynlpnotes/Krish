# Dockers and What is containers

* &#x20;If a developer is working on windows machine, so we will install all the dependencies for the project
* If another developer joins and he is using linux machine, then he needs to install dependencies
* There can be some library mismatch and so application does not install
* Somehow this is fixed and is moved to QA
* It might happen QA installation might miss some of the installation, so application might not work
* This used to happen before we started using containers
* Everything had to be done manually and might miss something
*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

**Containers:**

* A way to package application with all the necessary dependencies and configuration
* It is a portable artifact - we can easily share and move this package to any environment
* Makes development and deployment more easy and efficient
* We can move the container from Dev -> QA -> Prod
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

What is Docker?

* It is an open platform for developing, shipping and running applications
* Enables to separate application from infrastructure&#x20;
* Provides the ability to package and run an application in a loosely isolated environment called a container
