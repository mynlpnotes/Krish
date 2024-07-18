# Docker image vs Containers

* Application is having lots of dependencies and configuration
* In container we create layers of images
* Base image can be linux
* MongoDB or MySQL image will also be added as per requirement
* Python 3.7 image
* If we take this entire layer of images then this is called docker image
*   Once we have this docker image and run it, internally it will create a container which will have environment, considering all the dependencies it will try to run the application

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
