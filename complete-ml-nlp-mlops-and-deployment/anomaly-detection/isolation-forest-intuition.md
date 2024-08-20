# Isolation Forest Intuition

* To detect outliers
* When outlier is the most important in a use case
* Example is when we use bank account from different country than usual
* To detect if a person has cancer

**Isolation Forest:**

* Even though it is unsupervised, we will be using DT inside
* It will create DT using various features
* And the split will happen such that, for every data point will try to create a leaf node
* Outlier will be made completely isolated
* For every data point, we will calculate anomaly score
* If it crosses a threshold, then we consider it as a threshold
*

    <figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;
*

    <figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>


* Contamination is the proportion of outliers in the dataset. Used when fitting to define the threshold on the score of the samples
* if auto - then it will be used as per the paper
* We can also specify any value between 0 and 0.5

```python
from sklearn.ensemble import IsolationForest

clf = IsolationForest(contamination=0.2)
clf.fit(df)
predictions = clf.predict(df)

import numpy as np
index = np.where(predictions < 0)
index
```

*

    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
