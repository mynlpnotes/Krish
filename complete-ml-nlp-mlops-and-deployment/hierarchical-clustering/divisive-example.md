# Divisive Example

#### Example Data Points in 2D

1. ( A = (1, 1) )
2. ( B = (2, 1) )
3. ( C = (4, 4) )
4. ( D = (5, 4) )
5. ( E = (8, 8) )

#### Steps of Divisive Clustering

1. **Start with All Points in One Cluster**:
   * <mark style="color:purple;background-color:purple;">**Initially, all points ( {A, B, C, D, E} ) are grouped into a single cluster.**</mark>
2. **First Split**:
   * <mark style="color:purple;background-color:purple;">**Identify the two most dissimilar points in this cluster.**</mark> Here, **points ( A = (1, 1) ) and ( E = (8, 8) )** are the most distant.
   * <mark style="color:purple;background-color:purple;">**Split the points into two clusters based on their proximity**</mark> to either ( A ) or ( E ):
     * **Cluster 1**: ( {A, B} ) (closer to ( A ))
     * **Cluster 2**: ( {C, D, E} ) (closer to ( E ))
3. **Second Split**:
   * <mark style="color:purple;background-color:purple;">**Now, focus on the larger cluster, ( {C, D, E} ), and find the two most distant points within it**</mark> (here, ( C = (4, 4) ) and ( E = (8, 8) )).
   * Split ( {C, D, E} ) based on proximity to ( C ) or ( E ):
     * **Cluster 1**: ( {A, B} )
     * **Cluster 2a**: ( {C, D} ) (closer to ( C ))
     * **Cluster 2b**: ( {E} ) (closer to ( E ))
4. **Third Split**:
   * Finally, if needed, split ( {C, D} ). Since ( C ) and ( D ) are the only points left in this cluster, they can be separated as well:
     * **Cluster 1**: ( {A, B} )
     * **Cluster 2a**: ( {C} )
     * **Cluster 2b**: ( {D} )
     * **Cluster 2c**: ( {E} )

***

#### Summary of Final Clusters

The final clusters after all splits are:

1. ( {A, B} )
2. ( {C} )
3. ( {D} )
4. ( {E} )

***

#### Final Dendrogram Representation

The dendrogram for divisive clustering would look like this:

```
           [A B C D E]
              /     \
           [A B]   [C D E]
                   /     \
                [C D]    [E]
               /     \
             [C]     [D]
```

In divisive clustering, this structure represents how clusters are split from a single, all-inclusive cluster down to individual data points.
