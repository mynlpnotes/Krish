# Ball Tree Algorithm

| **Step**                          | **Description**                                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **1. Start with All Points**      | - Compute the **centroid** (mean of all points).                                                              |
|                                   | - Calculate the **radius** (maximum distance from centroid to any point).                                     |
| **2. Check Stopping Criteria**    | - If the number of points ≤ threshold (e.g., 1), stop and create a **leaf node**.                             |
| **3. Split the Data**             | - Find the **two farthest points** in the dataset to maximize separation.                                     |
|                                   | - Assign points to the group of the **nearest farthest point** (using distance metric).                       |
| **4. Recursively Build Subtrees** | - For each group, compute the **centroid** and **radius**, then repeat the splitting process.                 |
|                                   | - Stop when all nodes meet the stopping criteria.                                                             |
| **Querying the Ball Tree**        |                                                                                                               |
| **1. Start at the Root Node**     | - Calculate the **distance** between the query point and the centroid.                                        |
|                                   | - Check if the query lies within the root ball's radius.                                                      |
| **2. Traverse Subtrees**          | - Visit the **subtree** whose centroid is closest to the query point.                                         |
|                                   | - Continue until reaching a **leaf node**.                                                                    |
| **3. Prune Other Branches**       | - Eliminate branches where the minimum distance from the query to the ball exceeds the current best distance. |
