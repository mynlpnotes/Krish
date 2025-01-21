# Example using Gini

#### **Step 1: Dataset**

| **A** | **B** | **C** |
| ----- | ----- | ----- |
| Red   | X     | Yes   |
| Red   | Y     | No    |
| Blue  | X     | Yes   |
| Blue  | Y     | No    |
| Green | X     | Yes   |
| Green | Y     | No    |
| Red   | X     | No    |

***

#### **Step 2: Calculate Gini for the Entire Dataset**

For output variable **C** (Yes, No):

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 3         | 3/7 = 0.4286        | 0.2449     |
| No            | 4         | 4/7 = 0.5714        | 0.3265     |
| **Total**     | 7         |                     | **0.5714** |

***

#### **Step 3: Gini for Input Variable A (Red/Blue/Green)**

**Subset where A = Red:**

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 1         | 1/3 = 0.3333        | 0.2222     |
| No            | 2         | 2/3 = 0.6667        | 0.2222     |
| **Total**     | 3         |                     | **0.4444** |

**Subset where A = Blue:**

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 1         | 1/2 = 0.5           | 0.25       |
| No            | 1         | 1/2 = 0.5           | 0.25       |
| **Total**     | 2         |                     | **0.5**    |

**Subset where A = Green:**

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 1         | 1/2 = 0.5           | 0.25       |
| No            | 1         | 1/2 = 0.5           | 0.25       |
| **Total**     | 2         |                     | **0.5**    |

***

#### **Step 4: Weighted Gini for A (Red/Blue/Green)**

| **Subset (A)** | **Weight (count/total)** | **Gini** | Weighted Gini |
| -------------- | ------------------------ | -------- | ------------- |
| A = Red        | 3/7 = 0.4286             | 0.4444   | 0.1905        |
| A = Blue       | 2/7 = 0.2857             | 0.5      | 0.1429        |
| A = Green      | 2/7 = 0.2857             | 0.5      | 0.1429        |
| **Total**      |                          |          | **0.4763**    |

***

#### **Step 5: Gini for Input Variable B (X/Y)**

**Subset where B = X:**

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 3         | 3/4 = 0.75          | 0.1875     |
| No            | 1         | 1/4 = 0.25          | 0.1875     |
| **Total**     | 4         |                     | **0.375**  |

**Subset where B = Y:**

| **Class (C)** | **Count** | **Probability (p)** | ( p(1-p) ) |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 0         | 0                   | 0          |
| No            | 3         | 3/3 = 1             | 0          |
| **Total**     | 3         |                     | **0**      |

***

#### **Step 6: Weighted Gini for B (X/Y)**

| **Subset (B)** | **Weight (count/total)** | **Gini** | Weighted Gini |
| -------------- | ------------------------ | -------- | ------------- |
| B = X          | 4/7 = 0.5714             | 0.375    | 0.2143        |
| B = Y          | 3/7 = 0.4286             | 0.0      | 0.0           |
| **Total**      |                          |          | **0.2143**    |

***

#### **Step 7: Gini Gain for A and B**

| **Input Variable** | **Gini of the Entire Dataset** | **Weighted Gini** | **Gini Gain** |
| ------------------ | ------------------------------ | ----------------- | ------------- |
| A                  | 0.5714                         | 0.4763            | 0.0951        |
| B                  | 0.5714                         | 0.2143            | 0.3571        |

***

#### **Step 8: Build the Decision Tree (Level 1)**

Since **B** has the higher Gini gain (0.3571 vs 0.0951), we choose **B** as the root of the tree.

```
           B
        /     \
       X       Y
     /   \
  Yes   No
```

***

#### **Step 9: Recursively Build the Decision Tree (Level 2)**

**Subset where B = X:**

| **A** | **B** | **C** |
| ----- | ----- | ----- |
| Red   | X     | Yes   |
| Blue  | X     | Yes   |
| Green | X     | Yes   |
| Red   | X     | No    |

* For **B = X**, we can split further based on **A**:
  * **A = Red**: Gini = 0.4444 (1 Yes, 2 No)
  * **A = Blue**: Gini = 0 (All Yes)
  * **A = Green**: Gini = 0 (All Yes)

**Subset where B = Y:**

| **A** | **B** | **C** |
| ----- | ----- | ----- |
| Red   | Y     | No    |
| Blue  | Y     | No    |
| Green | Y     | No    |

* For **B = Y**, all instances are **No**, so no further splitting is needed.

***

#### **Final Decision Tree (2 Levels)**

```
           B
        /     \
       X       Y
     /   \
  Yes   No
```
