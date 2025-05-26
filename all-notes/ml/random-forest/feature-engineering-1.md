# Feature Engineering

* Data cleaning same as that done in classification

```python
##Check features with nan value
df.isnull().sum()

## Remove Unnecessary Columns
df.drop('car_name', axis=1, inplace=True)
df.drop('brand', axis=1, inplace=True)

df['model'].unique() # 120 values

# Get count of categorical, numerical (Discrete and continuous)

## Indpendent and dependent features
from sklearn.model_selection import train_test_split
X = df.drop(['selling_price'], axis=1)
y = df['selling_price']

# We will be using label encoding here, coz then it will try to find the relationship
# between label and selling price

from sklearn.preprocessing import LabelEncoder
le=LabelEncoder()
X['model']=le.fit_transform(X['model'])


# Use column transformation, apply one hot encoding and standard scalar

X=preprocessor.fit_transform(X)


```
