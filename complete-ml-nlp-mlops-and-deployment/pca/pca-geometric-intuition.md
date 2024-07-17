# PCA Geometric Intuition

* &#x20;Plot size of house vs No. of rooms
* As size increases, no. of rooms also increases
* We want to reduce this 2D to 1D using PCA
* We will project all this points into x-axis, then obviously this will get converted into 1D
* The area between 1st and last points is spread
* As spread increases, variance increases
* If we do like this size information is captured, no. of rooms information is lost
* In PCA we do some transformation on x axis and y-axis
* We apply eigen decomposition on some matrix -> Using this we will get new axis
* And then we will project this information into this axis
* new size and no.of rooms axis will get created
* We see the spread is properly captured on new size axis
* and the spread which will be projected on new no. of rooms of sizes which will be lost, will be very very loss
* Maximum variances is getting captured on new size axis
* This is better because comparatively the variances on y-axis which will be lost is low
* Our main aim is to find in PCA is to find axis which will be found after transformation
* We get PC1 and PC2 here
* If we have 3 dimensions, then we will have PC3 also
* PC1 will always carry maximum variance, followed by PC2 and so on
*

    <figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
* &#x20;Final aim is to get the best principal component, which captures maximum variance
*

    <figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>
