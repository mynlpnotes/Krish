---
hidden: true
---

# Example - Skip

*

    <figure><img src="../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>
* Epsilon and min points are hyperparameters
* If epsilon is very high then we will get 1 big cluster
* If min points is very high then we might end up with no cluster
* **Code:**
  * dbscan = DBSCAN(eps = 0.5, min\_samples = 5)
  * dbscan.fit()
  * dbscan.labels\_
  * -1 means outlier/noise
