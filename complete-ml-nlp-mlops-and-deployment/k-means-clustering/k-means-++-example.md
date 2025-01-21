# K-means ++ Example

#### Data Points (in 2D)

We have the following points:

1. ( A = (1, 2) )
2. ( B = (2, 3) )
3. ( C = (3, 4) )
4. ( D = (5, 8) )
5. ( E = (8, 8) )

We’ll select 3 centroids using **K-means++**.

***

#### Step 1: Randomly Select the First Centroid

Let’s randomly select **Point A = (1, 2)** as the first centroid.

* **Centroid 1**: ( (1, 2) )

***

#### Step 2: Calculate Squared Distances to the Closest Centroid

Calculate the squared distances between each point and **Centroid 1**. Record the squared distances in the table.

| Point | Coordinates | Distance to Centroid 1 (1, 2) | Squared Distance |
| ----- | ----------- | ----------------------------- | ---------------- |
| B     | (2, 3)      | ( \sqrt{2} )                  | 2                |
| C     | (3, 4)      | ( \sqrt{8} )                  | 8                |
| D     | (5, 8)      | ( \sqrt{52} )                 | 52               |
| E     | (8, 8)      | ( \sqrt{85} )                 | 85               |

#### Step 3: Select the Second Centroid Based on Probability

Calculate the probability for each point based on the squared distances. Higher distance values mean a higher chance of being selected. Assume **Point E = (8, 8)** is chosen as the second centroid.

* **Centroid 2**: ( (8, 8) )

***

#### Step 4: Calculate Squared Distances to the Nearest Centroid for Third Selection

Calculate the squared distances of each point to the nearest of the two centroids (( (1, 2) ) and ( (8, 8) )).

| Point | Coordinates | Distance to Closest Centroid | Squared Distance |
| ----- | ----------- | ---------------------------- | ---------------- |
| B     | (2, 3)      | ( \sqrt{2} )                 | 2                |
| C     | (3, 4)      | ( \sqrt{8} )                 | 8                |
| D     | (5, 8)      | ( \sqrt{9} )                 | 9                |

#### Step 5: Select the Third Centroid Based on Probability

Calculate the probability for each point based on the new squared distances. Assume **Point D = (5, 8)** is chosen as the third centroid.

* **Centroid 3**: ( (5, 8) )
