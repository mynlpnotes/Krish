# K Means clustering geometric intuition

* &#x20;If we have data points as on the left, then we can say that there are 2 groups
* Then after applying k means, it will form 2 clusters
* There will be centroild for each cluter
* For the 2nd examples, there are 3 groups
* Aim is to cluster similar points together
*

    <figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Steps:

1. Initialize some centroids - some k values
2. Find distance between all points and centroids - Check point is nearer to which centroid - Distance will be calculated using eucledian or manhattan distance

* All the points below the line are nearer to yellow centroid, the points above line are nearer to red centroid

3. Move the centroids - by taking average of all the points in the cluster

* &#x20;Again we repeat steps 2 and 3
*

    <figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>
