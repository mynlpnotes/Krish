# How DBSCAN works

* Red is core point
* Yellow is border point
* Blue is outlier
* Lets consider min points = 4 here and radius
* Based on density, clustering is done
* <mark style="color:purple;background-color:purple;">**Noise/Outlier are handled easily**</mark>
* <mark style="color:purple;background-color:purple;">**Can be used to cluster non linear data also**</mark>



* <mark style="color:purple;background-color:purple;">**Core point: If there are at least min points with a radius of epsilon**</mark>
* <mark style="color:purple;background-color:purple;">**Border Point: No. of data points within the radius will be less than min. points**</mark>
* <mark style="color:purple;background-color:purple;">**Outlier Point: No other point within the radius**</mark>



<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
