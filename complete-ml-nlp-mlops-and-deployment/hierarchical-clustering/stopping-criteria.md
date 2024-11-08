# Stopping Criteria

**1. Agglomerative Hierarchical Clustering**

* **Desired Number of Clusters**:\
  <mark style="color:purple;background-color:purple;">**The algorithm stops once the specified number of clusters is reached**</mark>. For example, if you want 3 clusters, the process stops when only 3 clusters remain.
* **Distance Threshold**:\
  The algorithm stops <mark style="color:purple;background-color:purple;">**when the distance between the closest clusters exceeds a predefined threshold**</mark> (e.g., a specified Euclidean distance). This prevents further merging if the clusters are sufficiently distant from each other.

**2. Divisive Hierarchical Clustering**

* **Desired Number of Clusters**:\
  The algorithm stops <mark style="color:purple;background-color:purple;">**when the desired number of clusters is reached**</mark>, similarly to agglomerative clustering.
* **No Further Meaningful Splits**:\
  <mark style="color:purple;background-color:purple;">**The process halts when a cluster cannot be divided further without losing information or creating overly small**</mark>, homogeneous groups.
* **Quality of Split Drops Below Threshold**:\
  If further divisions do not improve cluster quality (e.g., no distinctiveness or compactness), the algorithm stops. This can be measured by metrics like intra-cluster variance or homogeneity.
