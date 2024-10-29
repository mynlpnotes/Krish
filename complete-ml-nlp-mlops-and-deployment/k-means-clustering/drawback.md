# Drawback

* Location of initialization of centroid
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* In this case, once the first centroid has got some data point, other centroid wont get any data point
* Solution:

1. K-mean ++

* Don’t place centroid as very close during initialization, there needs to be distance  between centroid

2. Instead of providing the entire dataset, provide data in batches

* Provide this batches while building the model
* This is knows as mini batch k mean



* By default  k mean ++ is used sklearn
* For clustering we use either agglomerative(Hierarchical)/divisive(K means) approach
* Kmean = Kmeans(n\_clusters)
* Kmean.fit()
* Kmean.inertia\_
* Mbatch = MiniBatchKMeans(n\_cluster = 5)
