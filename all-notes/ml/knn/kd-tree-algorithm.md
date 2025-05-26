# Kd Tree Algorithm

| **Step**                          | **Description**                                                                                                                  |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **1. Start with All Points**      | - Select the **median point** along one dimension (usually x-axis, then alternate dimensions).                                   |
|                                   | - Split the dataset into two subsets: points to the left of the median and points to the right.                                  |
| **2. Recursively Build Subtrees** | - Recursively apply the same process to the left and right subsets, alternating the splitting dimension at each level.           |
| **3. Stopping Criteria**          | - Stop splitting when a subset contains one point or meets a predefined minimum threshold (e.g., 1 point per leaf node).         |
| **Querying the KD Tree**          |                                                                                                                                  |
| **1. Start at the Root Node**     | - Compare the query point with the root's splitting dimension (e.g., x-axis).                                                    |
|                                   | - Decide whether to go to the **left** or **right** subtree based on the query point's value along the splitting dimension.      |
| **2. Traverse Subtrees**          | - Continue traversing down the tree recursively, checking the appropriate subtree based on the splitting dimension at each node. |
| **3. Prune Other Subtrees**       | - If necessary, prune subtrees that are too far from the query point (based on distance).                                        |
| **4. Return Nearest Neighbor**    | - Once a leaf node is reached, calculate the distance to the query point and return the closest neighbor.                        |
