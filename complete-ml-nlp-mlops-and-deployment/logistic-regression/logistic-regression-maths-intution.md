# Logistic Regression - Maths Intution

* &#x20;We have to squash the result between 0 and 1
* So for this we use sigmoid activation function
* If we use any z value still the value of sigmoid function will be between 0 and 1
* If z > 0 then sigmoid will be greater than 0.5
* So on the best fit line we will be applying activation function
* So due to this squashing for every outlier also it will give the value as 1&#x20;
*

    <figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
* &#x20;If we use the similar cost function as linear regression then we will not get a convex function, and there will be multiple local minima
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* Instead we will be using log loss cost function here
* If we use this log loss then we will be getting convex function
*

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
* &#x20;Same steps repeated for convergence algorithm
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
*
