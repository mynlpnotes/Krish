# Introduction

* &#x20;If we are looking for real number or absolute value then in that case regression is good
* Logistic regression is used for <mark style="color:purple;background-color:purple;">**classification**</mark>
* Other algorithms like DT, RF etc can also be used for classification
* <mark style="color:purple;background-color:purple;">**We draw a line for separation of classes**</mark>
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Probability of finding whether the give data point will be on which side of the line 🡪 this is what the algorithm will learn**</mark>
* There can be multiple lines, but we need to the best fitted line
* Here also to draw the line we need m and c
* Can be used for multi class as well binary class
* Addition of probability of all the classes will be 1
* <mark style="color:purple;background-color:purple;">**Function for finding probability will be sigmoid**</mark>
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Output will always be between 0 and 1**</mark>
* Equation, y = m1x1 + m2x2 +c
* If we are able to find the value of m1, m2, then we can get the value of y, but here value of y will be real number, but we need probability
* P(class)  = 1 / (1 + e –(m1x1 + m2x2 + c))
* <mark style="color:purple;background-color:purple;">**We can set a threshold, if probability is less than 0.5 then its class 1 if greater then its class 2**</mark>
* After normalizing and probability of class 1 and 2
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Divide eq 1 and eq 2, and then take log on both the sides
* We are doing this all, to represent the entire line as logit function
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In log we need to take base e
* If P < 0.5, suppose its 0.4 then the output will be -0.17, it will give negative
* If P > 0.5 , for 0.7 then it will be 0.367, it will give positive
* If we have probability then we can predict the value of y
