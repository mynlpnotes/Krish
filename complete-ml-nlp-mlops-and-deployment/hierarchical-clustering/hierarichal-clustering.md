# Hierarichal clustering

* &#x20;Here we will be having same number of clusters
* <mark style="color:purple;background-color:purple;">**No centroids**</mark>
*

    <figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
* &#x20;2 Types - Agglomerative and Divisive clustering
* Agglomerative - Combining
* Divising - Division

**Steps for agglomerative:**

1. <mark style="color:purple;background-color:purple;">**For each data point, we will consider it as a separate class**</mark>
2. <mark style="color:purple;background-color:purple;">**Find the nearest point and create a new cluster**</mark>
3. <mark style="color:purple;background-color:purple;">**Keep on doing this till we get a single cluster**</mark>

*   &#x20;

    <figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>
* Creation of <mark style="color:purple;background-color:purple;">**dendrogram - Plot Euclidian distance vs points**</mark>
* Each point is a separate cluster
* Combine the point which are nearest - so we combine P4P5
* Then we combine P1P2
* Combine P6 and P4P5
* Combine P3 with P1P2
* Keep doing this till all the points are combined&#x20;
* <mark style="color:purple;background-color:purple;">**Look for a long horizontal line in the dendrogram without any merges below it (indicating a significant distance between clusters) -> Cut line**</mark>
* <mark style="color:purple;background-color:purple;">**Draw a horizontal line across the dendrogram at this height to "cut" the tree. This cut determines the number of clusters**</mark>
*

    <figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>
