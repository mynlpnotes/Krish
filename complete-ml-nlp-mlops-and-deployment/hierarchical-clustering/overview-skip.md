---
hidden: true
---

# Overview - Skip

* Also known as agglomerative approach
* We start n data points so there will be n clusters
* And then we will start combining data points
* No need to know value of K before hand
* This is bottom approach
* Plot all the points
* Treat all the points as individual clusters
* Which point is closer to P1?
  * If P1 and P2 are the closest then draw vertical line between them
  * The length of vertical line is the similarity measure (Euclidean distance)
  * Once done all the points then take the centroid of each vertical lines and then repeat the same
* This is known as dendogram
* Find the biggest vertical line, so from the mean of it, we will draw a horizontal line
* The number of points at which it will be intersecting, that many number of cluster will be there
* We select the biggest vertical line, because it represents actual distance between clusters
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

