# Silhoutte Clustering Intuition

* Silhoutte scoring will help to validate unsupervised ml algo like k means
* For every data point in a cluster, compute average distance of a point to all clusters in the same cluster -> a(i)
* Take the nearest cluster C2, for the same point find the average distance of the point to all the points in C2 -> b(i)
*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
* &#x20;if a(i) << b(i) -> clustering is done well
*   &#x20;if a(i) >> b(i) -> clustering is not done well

    <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
* &#x20;Silhoutte sciore will be between -1 and +1
* if it near to +1 better clustering model has been created
*

    <figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
