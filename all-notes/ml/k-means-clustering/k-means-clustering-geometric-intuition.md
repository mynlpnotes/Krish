# K Means clustering geometric intuition

* If we have data points as on the left, then we can say that there are 2 groups
* Then after applying k means, it will form 2 clusters
* There will be centroid for each cluster
* For the 2nd examples, there are 3 groups
* Aim is to cluster similar points together
*

    <figure><img src="../../../.gitbook/assets/image (305).png" alt=""><figcaption></figcaption></figure>

**Steps:**

1. <mark style="color:purple;background-color:purple;">**Initialize some centroids - some k values**</mark>
2. <mark style="color:purple;background-color:purple;">**Find distance between all points and centroids - Check point is nearer to which centroid - Distance will be calculated using Euclidean or Manhattan distance**</mark>
3. <mark style="color:purple;background-color:purple;">**Move the centroids - by taking average of all the points in the cluster**</mark>
4. <mark style="color:purple;background-color:purple;">**Again we repeat steps 2 and 3**</mark>
5. <mark style="color:purple;background-color:purple;">**For new data point, we will see the nearest centroid and place it in that cluster**</mark>

<figure><img src="../../../.gitbook/assets/image (306).png" alt=""><figcaption></figcaption></figure>
