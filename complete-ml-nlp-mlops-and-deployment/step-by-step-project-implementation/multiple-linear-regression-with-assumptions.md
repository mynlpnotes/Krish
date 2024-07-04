# Multiple Linear Regression with Assumptions

{% embed url="https://github.com/krishnaik06/Complete-Data-Science-With-Machine-Learning-And-NLP-2024/blob/main/5-Step%20By%20Step%20Project%20Implementation%20With%20LifeCycle%20Of%20ML%20Projects/4.0-Multiple%20Linear%20Regression.ipynb" %}

* Assumptions same as that in simple linear

```python
from sklearn.datasets import fetch_california_housing

california=fetch_california_housing()
california.keys()
# dict_keys(['data', 'target', 'frame', 'target_names', 'feature_names', 'DESCR'])

print(california.DESCR)

california.data
california.target

dataset=pd.DataFrame(california.data,columns=california.feature_names)
dataset['Price']=california.target

dataset.info()
dataset.isnull().sum()
dataset.describe()

# Check missing values
# Check if there is some correlation
# Split the data
# Standardize the data
# Model training
# Performance metrics on test data
# Check the assumptions
# Pickle the model
```
