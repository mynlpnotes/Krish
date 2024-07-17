# Hierarichal clustering

* &#x20;Here we will be having same number of clusters, but there wont be any centroids
*

    <figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
* &#x20;2 Types - Agglomerative and Divisive clustering
* Agglomerative - Combining
* Divising - Division

Steps for agglomerative:

1. For each data point, we will consider it as a separate class
2. Find the nearest point and create a new cluster
3. Keep on doing this till we get a single cluster

*   &#x20;

    <figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
* Creation of dendogram - Plot eucledian distance vs points
* Each point is a separate cluster
* Combine the point which are nearest - so we combine P4P5
* Then we combine P1P2
* Combine P6 and P4P5
* Combine P3 with P1P2
* Keep doing this till all the points are combined&#x20;
*
*
*

    <figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
