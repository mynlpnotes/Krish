# How DBSCAN works

* Red is core point
* Yellow is border point
* Blue is outlier
* Lets consider min points = 4 here and radius
* Based on density, clustering is done
* Noise/Outlier are handled easily
* Can be used to cluster non linear data also

Core point: If there are atleast min points with a radius of epsilon

Border Point: No. of data points within the radius will be less than min. points

Outlier Point: No other point within the radius



<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
