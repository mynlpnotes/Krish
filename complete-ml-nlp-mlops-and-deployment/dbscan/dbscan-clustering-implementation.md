# DBSCAN Clustering Implementation

```python
from sklearn.cluster import DBSCAN
from sklearn.datasets import make_moons

X,y=make_moons(n_samples=250,noise=0.05) # To make data

X_scaled=scaler.fit_transform(X)

dbcan=DBSCAN(eps=0.3)
dbcan.fit(X_scaled)
dbcan.labels_ # To get the cluster for each point


```

*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
