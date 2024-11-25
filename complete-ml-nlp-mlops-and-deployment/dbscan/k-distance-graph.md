# K-distance Graph



* <mark style="color:purple;background-color:purple;">**Step 1: Define Data Points**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**Step 2: Calculate Distances Between All Points**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**Step 3: Find the 4th Nearest Neighbor for Each Point**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**Step 4: Sort the 4th Nearest Neighbor Distances**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**Step 5: Interpret the "Elbow" in the Sorted Distances**</mark>
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>



**8 data points** and **k = 4** (since `min_samples = 5`, so k = 4 means the distance to each point’s **4th nearest neighbor**).

#### Step 1: Define Data Points

Consider the following **8 points in a 2D space**: \[ \text{Data points} = {(1, 1), (2, 1), (4, 3), (5, 4), (8, 8), (1, 5), (7, 5), (9, 9)} ]

#### Step 2: Calculate Distances Between All Points

Using the Euclidean distance formula, we calculate the distance between each pair of points.

**Distance Matrix (Rounded to 2 Decimal Places)**

| Point | (1,1) | (2,1) | (4,3) | (5,4) | (8,8) | (1,5) | (7,5) | (9,9) |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| (1,1) | 0     | 1.00  | 3.61  | 5.00  | 9.89  | 4.00  | 7.21  | 11.31 |
| (2,1) | 1.00  | 0     | 2.83  | 4.24  | 9.22  | 4.12  | 6.32  | 10.63 |
| (4,3) | 3.61  | 2.83  | 0     | 1.41  | 5.66  | 4.47  | 3.16  | 7.21  |
| (5,4) | 5.00  | 4.24  | 1.41  | 0     | 5.00  | 5.39  | 2.00  | 6.40  |
| (8,8) | 9.89  | 9.22  | 5.66  | 5.00  | 0     | 8.06  | 3.16  | 1.41  |
| (1,5) | 4.00  | 4.12  | 4.47  | 5.39  | 8.06  | 0     | 6.32  | 10.00 |
| (7,5) | 7.21  | 6.32  | 3.16  | 2.00  | 3.16  | 6.32  | 0     | 4.24  |
| (9,9) | 11.31 | 10.63 | 7.21  | 6.40  | 1.41  | 10.00 | 4.24  | 0     |

#### Step 3: Find the 4th Nearest Neighbor for Each Point

Since **k = 4**, we’ll find the distance to the **4th nearest neighbor** for each point. Ignore the zero distance to each point itself, then find the 4th smallest distance in each row.

* **Point (1,1)**: 4th nearest neighbor is (1,5) with distance **4.00**
* **Point (2,1)**: 4th nearest neighbor is (1,5) with distance **4.12**
* **Point (4,3)**: 4th nearest neighbor is (1,5) with distance **4.47**
* **Point (5,4)**: 4th nearest neighbor is (8,8) with distance **5.00**
* **Point (8,8)**: 4th nearest neighbor is (5,4) with distance **5.00**
* **Point (1,5)**: 4th nearest neighbor is (8,8) with distance **8.06**
* **Point (7,5)**: 4th nearest neighbor is (9,9) with distance **4.24**
* **Point (9,9)**: 4th nearest neighbor is (7,5) with distance **4.24**

#### Step 4: Sort the 4th Nearest Neighbor Distances

Now we take the distances to each point's 4th nearest neighbor and sort them:

\[ {4.00, 4.12, 4.47, 5.00, 5.00, 8.06, 4.24, 4.24} -> text{Sorted: } {4.00, 4.12, 4.24, 4.24, 4.47, 5.00, 5.00, 8.06} ]

#### Step 5: Interpret the "Elbow" in the Sorted Distances

When plotting these sorted distances, the **"elbow"** point represents a suitable choice for `ε`:

* **Sorted distances**: \[4.00, 4.12, 4.24, 4.24, 4.47, 5.00, 5.00, 8.06]
* **Interpretation**: The distances increase gradually but start to jump noticeably after **4.47**.

Thus, an **optimal `ε`** value might be around **4.47**, as it represents the point before distances start to increase more sharply, balancing cluster density and separation.
