# Optimization of KNN -KDTree and Ball Tree intuition

* &#x20;We should not check the distance with each and every point, we should create binary tree
* We 1st find the median of f1 and f2
* We will draw a line from median of f1 to the x axis, so we get 2 regions
* We will round off median to the nearest actual point
* We 1st split from 7,2 to x axis
* Now we will draw a line from median of f2 to the y axis
* We split 5,4 to y axis
* Now we take region to the left&#x20;
* Take the median of f1 and f2 and do divisions
* Similarly we will keep on doing divisions
* Using this divisons we will create a binary tree
* For the new test data, we can know to which region it belongs
* From the point, we will traverse back and find the nearest points
*

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
* &#x20;Group all the nearest point together
* So we group 1,2 and then 3,4 and then 5,6,7 and 8, 9
* Now combine nearest groups
*

    <figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
