# Silhoutte Intuition

* Silhouette scoring will help to validate unsupervised ml algo like k means
* <mark style="color:purple;background-color:purple;">**For every data point in a cluster, compute average distance of a point to all clusters in the same cluster -> a(i)**</mark>
* <mark style="color:purple;background-color:purple;">**Take the nearest cluster C2, for the same point find the average distance of the point to all the points in C2 -> b(i)**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (260).png" alt=""><figcaption></figcaption></figure>
* &#x20;<mark style="color:purple;background-color:purple;">**if a(i) << b(i) -> clustering is done well**</mark>
*   &#x20;<mark style="color:purple;background-color:purple;">**if a(i) >> b(i) -> clustering is not done well**</mark>

    <figure><img src="../../../.gitbook/assets/image (261).png" alt=""><figcaption></figcaption></figure>
* &#x20;<mark style="color:purple;background-color:purple;">**Silhouette score will be between -1 and +1**</mark>
* <mark style="color:purple;background-color:purple;">**if it near to +1 better clustering model has been created**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (262).png" alt=""><figcaption></figcaption></figure>
