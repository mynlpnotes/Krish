# Silhoutte Diagram

* Plot every instance’s silhouette coefficient, sorted by the cluster they are assigned to and by the value of the coefficient
* Each diagram contains one knife shape per cluster.&#x20;
* The shape’s height indicates the number of instances the cluster contains, and its width represents the sorted silhouette coefficients of the instances in the cluster (wider is better).&#x20;
* The dashed line indicates the mean silhouette coefficient
* <mark style="color:purple;background-color:purple;">**Long bars to the right**</mark> <mark style="color:purple;background-color:purple;"></mark><mark style="color:purple;background-color:purple;">(towards +1) indicate points that are well-clustered.</mark>
* <mark style="color:purple;background-color:purple;">**Bars near 0**</mark> <mark style="color:purple;background-color:purple;"></mark><mark style="color:purple;background-color:purple;">indicate points that are on the boundary between clusters.</mark>
* <mark style="color:purple;background-color:purple;">**Bars to the left**</mark> <mark style="color:purple;background-color:purple;"></mark><mark style="color:purple;background-color:purple;">(towards -1) would indicate misclassified points (though there aren't any in this case).</mark>
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* The vertical dashed lines represent the silhouette score for each number of clusters.&#x20;
* When most of the instances in a cluster have a lower coefficient than this score (i.e., if many of the instances stop short of the dashed line, ending to the left of it), then the cluster is rather bad since this means its instances are much too close to other clusters
