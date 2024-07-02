# Handling Imbalanced Dataset

* Lets say we have a binary classification
* We have 1000 datapoints
* Out of this we have 900 Yes and 100 No
* So here maximum datapoints is Yes
* This is imbalanced dataset
* Model which we are training will get biased to max class

1. Upsampling: Increase the minority class datapoint
2. Downsampling: Reduce the majority class datapoints, bad as we losing data

```python
## upsampling
df_minority=df[df['target']==1]
df_majority=df[df['target']==0]

from sklearn.utils import resample
df_minority_upsampled=resample(df_minority,replace=True, #Sample With replacement
         n_samples=len(df_majority),
         random_state=42
        )
df_upsampled=pd.concat([df_majority,df_minority_upsampled])

# Downsampling
from sklearn.utils import resample
df_majority_downsampled=resample(df_majority,replace=False, #Sample With replacement
         n_samples=len(df_minority),
         random_state=42
        )
```
