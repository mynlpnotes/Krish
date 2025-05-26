# Example using Entropy

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

#### **Step 2: Calculate the Entropy of the Entire Dataset**

| **Class (C)** | **Count** | **Probability ( p\_i )** | $$( p_i \log_2(p_i) )$$ |
| ------------- | --------- | ------------------------ | ----------------------- |
| Yes           | 3         | $$( \frac{3}{7} )$$      | ( -0.528 )              |
| No            | 4         | $$( \frac{4}{7} )$$      | ( -0.389 )              |
| **Total**     | 7         |                          | **0.985**               |

***

#### **Step 3: Entropy for Input Variable A (Red/Blue/Green)**

**Subset where A = Red**

| **Class (C)** | **Count** |                     |            |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 1         | $$( \frac{1}{3} )$$ | ( -0.528 ) |
| No            | 2         | $$( \frac{2}{3} )$$ | ( -0.389 ) |
| **Total**     | 3         |                     | **0.918**  |

**Subset where A = Blue**

| **Class (C)** | **Count** |                     |          |
| ------------- | --------- | ------------------- | -------- |
| Yes           | 1         | $$( \frac{1}{2} )$$ | ( -0.5 ) |
| No            | 1         | $$( \frac{1}{2} )$$ | ( -0.5 ) |
| **Total**     | 2         |                     | **1.0**  |

**Subset where A = Green**

| **Class (C)** | **Count** |                     |          |
| ------------- | --------- | ------------------- | -------- |
| Yes           | 1         | $$( \frac{1}{2} )$$ | ( -0.5 ) |
| No            | 1         | $$( \frac{1}{2} )$$ | ( -0.5 ) |
| **Total**     | 2         |                     | **1.0**  |

***

#### **Step 4: Weighted Entropy for Input A (Red/Blue/Green)**

| **Subset (A = Red/Blue/Green)** | **Weight (count/total)**     | **Entropy** | Weighted Entropy |
| ------------------------------- | ---------------------------- | ----------- | ---------------- |
| A = Red                         | $$( \frac{3}{7} = 0.4286 )$$ | 0.918       | 0.393            |
| A = Blue                        | $$( \frac{2}{7} = 0.2857 )$$ | 1.0         | 0.286            |
| A = Green                       | $$( \frac{2}{7} = 0.2857 )$$ | 1.0         | 0.286            |
| **Total**                       |                              |             | **0.965**        |

***

#### **Step 5: Entropy for Input Variable B (X/Y)**

**Subset where B = X**

| **Class (C)** | **Count** |                     |            |
| ------------- | --------- | ------------------- | ---------- |
| Yes           | 3         | $$( \frac{3}{7} )$$ | ( -0.528 ) |
| No            | 1         | $$( \frac{1}{7} )$$ | ( -1.807 ) |
| **Total**     | 4         |                     | **1.540**  |

**Subset where B = Y**

| **Class (C)** | **Count** |                     |       |
| ------------- | --------- | ------------------- | ----- |
| Yes           | 0         | 0                   | 0     |
| No            | 3         | $$( \frac{3}{3} )$$ | 0     |
| **Total**     | 3         |                     | **0** |

***

#### **Step 6: Weighted Entropy for Input B (X/Y)**

| **Subset (B = X/Y)** | **Weight (count/total)**     | **Entropy** | Weighted Entropy |
| -------------------- | ---------------------------- | ----------- | ---------------- |
| B = X                | $$( \frac{4}{7} = 0.5714 )$$ | 1.540       | 0.879            |
| B = Y                | $$( \frac{3}{7} = 0.4286 )$$ | 0.0         | 0.0              |
| **Total**            |                              |             | **0.879**        |

***

#### **Step 7: Information Gain for A and B**

| **Input Variable** | **Entropy of the Entire Dataset** | **Weighted Entropy** | **Information Gain** |
| ------------------ | --------------------------------- | -------------------- | -------------------- |
| A                  | 0.985                             | 0.965                | 0.020                |
| B                  | 0.985                             | 0.879                | 0.106                |

***

#### **Step 8: Build the Decision Tree (Level 1)**

Since **B** has the higher information gain (0.106 vs 0.020), we choose **B** as the root of the tree.

| **Decision Tree** |
| ----------------- |
| B                 |
| / \\              |
| X Y               |

***

#### **Step 9: Recursively Build the Decision Tree (Level 2)**

**Subset where B = X**

| **A** | **B** | **C** |
| ----- | ----- | ----- |
| Red   | X     | Yes   |
| Blue  | X     | Yes   |
| Green | X     | Yes   |
| Red   | X     | No    |

* For **B = X**, we can split further based on **A**.

| **Subset for B = X** | **Next Split** |
| -------------------- | -------------- |
| Red                  | Yes/No         |
| Blue                 | Yes            |
| Green                | Yes            |

**Subset where B = Y**

| **A** | **B** | **C** |
| ----- | ----- | ----- |
| Red   | Y     | No    |
| Blue  | Y     | No    |
| Green | Y     | No    |

* For **B = Y**, all instances are **No**, so no further splitting is needed (pure class).

| **Subset for B = Y** | **Next Split** |
| -------------------- | -------------- |
| Red                  | No             |
| Blue                 | No             |
| Green                | No             |

***

#### **Final Decision Tree (2 Levels)**

```
       B
    /     \
   X       Y
 /   \
```

Yes No
