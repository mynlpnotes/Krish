# Feature Engineering

* Reduce unwanted columns
* Fields like pin code will be numeric but it will have fixed values, that's why we checking discrete and continuous features for numeric

```python
# create new column for feature
df['TotalVisiting'] = df['NumberOfPersonVisiting'] + 
                                df['NumberOfChildrenVisiting']
df.drop(columns=['NumberOfPersonVisiting', 'NumberOfChildrenVisiting'], 
                                axis=1, inplace=True)
                                
## get all the numeric features
num_features = [feature for feature in df.columns if df[feature].dtype != 'O']
print('Num of Numerical Features :', len(num_features))

##categorical features
cat_features = [feature for feature in df.columns if df[feature].dtype == 'O']
print('Num of Categorical Features :', len(cat_features))

## Discrete features
discrete_features=[feature for feature in num_features if len(df[feature].unique())<=25]
print('Num of Discrete Features :',len(discrete_features))

## coontinuous features
continuous_features=[feature for feature in num_features if feature not in discrete_features]
print('Num of Continuous Features :',len(continuous_features))


```

* To perform something to on a column we use columntransformer
*

```python
X = df.drop(['ProdTaken'], axis=1)
y = df['ProdTaken']

# Create Column Transformer with 3 types of transformers
cat_features = X.select_dtypes(include="object").columns
num_features = X.select_dtypes(exclude="object").columns

from sklearn.preprocessing import OneHotEncoder, StandardScaler
from sklearn.compose import ColumnTransformer

numeric_transformer = StandardScaler()
oh_transformer = OneHotEncoder(drop='first')

preprocessor = ColumnTransformer(
    [
         ("OneHotEncoder", oh_transformer, cat_features),
          ("StandardScaler", numeric_transformer, num_features)
    ]
)

X_train=preprocessor.fit_transform(X_train)
X_test=preprocessor.transform(X_test)
```
