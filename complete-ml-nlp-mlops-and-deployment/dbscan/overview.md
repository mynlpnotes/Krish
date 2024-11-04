# Overview

* Density based special cluster of application with noise
* Epsilon: Relative points
* Min points: Minimum points which we will be able to accommodate to create a cluster
* Core points: Which is going to satisfy minimum point criteria
* Border points: Which are part of a cluster, but are not going to form its own cluster
* Noise: Which is not part of any of the clusters
* We first define value for epsilon and min points
* Algorithm will start from any of the random points which are part of the dataset
* From the point, if we take circle of radius as epsilon, then we will check how many points are inside the circle
* If the no. of points inside the circle is less than min points, then it wont form a cluster at this point of time
* If we take another random point, and it satisfies min point criteria, then it forms a cluster and that point becomes core point
* Now we take all the points which are part of the cluster and then we draw circle for those points
* If those point does not satisfy the criteria then it does not extend the cluster
* If it satisfies the min points, then it creates a cluster and it becomes a core point and the same procedure is repeated
* Here we got 3 cluster using this
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
