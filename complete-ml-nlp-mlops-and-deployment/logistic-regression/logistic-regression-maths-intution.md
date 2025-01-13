# Logistic Regression - Maths Intution

* We have to <mark style="color:purple;background-color:purple;">**squash the result between 0 and 1 using sigmoid**</mark>
* If we use any z value still the value of sigmoid function will be between 0 and 1
* <mark style="color:purple;background-color:purple;">**If z > 0 then sigmoid will be greater than 0.5**</mark>
* <mark style="color:purple;background-color:purple;">**So on the best fit line we will be applying activation function**</mark>
* So due to this squashing for every outlier also it will give the value as 1&#x20;
*

    <figure><img src="../../.gitbook/assets/image (22) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;<mark style="color:purple;background-color:purple;">**If we use the similar cost function as linear regression then we will not get a convex function, and there will be multiple local minima**</mark>
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Instead <mark style="color:purple;background-color:purple;">**we will be using log loss cost function here as it gives a convex function**</mark>
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;Same steps repeated for convergence algorithm
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*
