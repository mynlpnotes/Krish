# K means clustering implementation

* K value can be validated using kneelocator or silhoutte scoring
* In silhoutte score, for whichever k we have highest silhoutte score we will take it as k

```python
# For making dataset
from sklearn.datasets import make_blobs
X,y=make_blobs(n_samples=1000,centers=3,n_features=2)

# View the data
plt.scatter(X[:,0],X[:,1],c=y)

## standardization--feature scaling technique
from sklearn.preprocessing import StandardScaler
scaler=StandardScaler()

X_train, X_test, y_train, y_test = train_test_split( X, y, 
    test_size=0.33, random_state=42)
    
X_train_scaled=scaler.fit_transform(X_train)
X_test_scaled=scaler.transform(X_test)

from sklearn.cluster import KMeans
## Elbow method To select K Value
wcss=[]
for k in range(1,11):
    kmeans=KMeans(n_clusters=k,init="k-means++")
    kmeans.fit(X_train_scaled)
    wcss.append(kmeans.inertia_)

## plot elbow curve
plt.plot(range(1,11),wcss)
plt.xticks(range(1,11))
plt.xlabel("Number of Clustrers")
plt.ylabel("WCSS")
plt.show()

kmeans=KMeans(n_clusters=3,init="k-means++")
kmeans.fit_predict(X_train_scaled)

y_pred=kmeans.predict(X_test_scaled)
plt.scatter(X_test[:,0],X_test[:,1],c=y_pred)

!pip install kneed
from kneed import KneeLocator
kl=KneeLocator(range(1,11),wcss,curve="convex",direction="decreasing")
kl.elbow # 3

from sklearn.metrics import silhouette_score
silhouette_coefficients=[]
for k in range(2,11):
    kmeans=KMeans(n_clusters=k,init="k-means++")
    kmeans.fit(X_train_scaled)
    score=silhouette_score(X_train_scaled,kmeans.labels_)
    silhouette_coefficients.append(score)

## plotting silhouette score
plt.plot(range(2,11),silhouette_coefficients)
plt.xticks(range(2,11))
plt.xlabel("Number of Cluters")
plt.ylabel("Silhoutte Coeffecient")
plt.show()

```

*

    <figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption><p>View the clusters</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption><p>Elbow plot</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Silhoutte score plot</p></figcaption></figure>
