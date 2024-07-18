# Pros and Cons of DBSCAN

**Advantage:**

1. Does not required to specify number of clusters
2. Can find arbitrarily shaped clusters, can also find a cluster surrounded by another cluster
3. Robust to outliers
4. Requires just 2 parameters
5. Min points and radius can be set by a domain expert, if the data is well understood

**Disadvantage:**

1. Not entirely deterministic. A border point reachable from one cluster can be part of another cluster also
2. Quality depends on distance measure used (Euclidean)
3. Cannot cluster with large differences in densities, since min points cannot be chosed appropriately for all the clusters
4. If the data and scale are not well understood, then choosing a meaningful radius will be difficult
