# Accuracy - Skip

* It should have interclass similarity
* Intraclass similarity should be very low
* **Rand index:**
* Total agree /  (Total disagree + Total agree)
* SS – Both the points belong to the same cluster for the algorithm and for ground truth - 1
* DD – Both point don’t belong the same cluster for both the algorithm and the ground truth – 0
* SD
*   DS

    |                             | Prediction from cluster |                      |                             |
    | --------------------------- | ----------------------- | -------------------- | --------------------------- |
    | Ground Truth                |                         | 1(Belong to cluster) | 0(Do not belong to cluster) |
    | 1(Belong to cluster)        | SS                      | SD                   |                             |
    | 0(Do not belong to cluster) | DS                      | DD                   |                             |


* Rand index = (SS + DD) / (SS + DD + SD + DS)
* Ground truth – sort of labelled data for the cluster
* **Jaccard coefficient:**
  * Total dataset which cluster is able to group from the ground truth
  * SS / (SS + SD + DS)
* **Entropy:**
  * -pi \* log (pi)
  * If entropy one cluster is high compared to another cluster, then we say one cluster is bad to another cluster
* **Purity:**
  * Total percentage of data points clustered successfully
  * Not implemented in sklearn yet
* **Silhouette coefficient:**
  * (b(x) – a(x)) / max ( a(x),b(x) )
  * a(x) – average distance of x from all the other points in the same cluster
  * b(x) – average distance of x from all the points in the other cluster
* other algos require ground truth data, whereas this does not
* if data point is in cluster then silhouette score will be very less
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```python
from sklearn import metrics
metrics.adjusted_rand_score()
metrics.jaccard_score()

```
