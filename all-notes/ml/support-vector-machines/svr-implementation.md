# SVR Implementation

* &#x20;Feature encoding -> Label encoding and Onehot encoding
* Whenever we have 2 categories we can use label encoding
* Whenever more than 2 categories are there we will be using One hot encoding
*

```python
df.columns -> # To get list of all the columns
## independnent and dependent features
X=df[['tip', 'sex', 'smoker', 'day', 'time', 'size']]
y=df['total_bill']

import warnings
warnings.filterwarnings('ignore')
X_train['sex']=le1.fit_transform(X_train['sex'])
X_train['smoker']=le2.fit_transform(X_train['smoker'])
X_train['time']=le3.fit_transform(X_train['time'])

## Onehot encoding--- ColumnTrnasformer
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
# 3 here suggests that one hot encoding needs to be applied to 3rd column
ct=ColumnTransformer(transformers=[('onehot',OneHotEncoder(drop='first'),[3])],
                                   remainder='passthrough')
# remainder = drop means drop all the other features apart from which are being encoded
# remainder = passthrough means keep other features also
X_train=ct.fit_transform(X_train)
X_test=ct.transform(X_test)

## SVR--Support Vector Regression
from sklearn.svm import SVR
svr=SVR()
svr.fit(X_train,y_train)
y_pred=svr.predict(X_test)

print(r2_score(y_test,y_pred))
print(mean_absolute_error(y_test,y_pred))

# Hyper parameter tuning
param_grid = {'C': [0.1, 1, 10, 100, 1000],
              'gamma': [1, 0.1, 0.01, 0.001, 0.0001],
              'kernel': ['rbf']}
grid = GridSearchCV(SVR(), param_grid, refit = True, verbose = 3)
grid.fit(X_train, y_train)
grid.best_params_
grid_prediction=grid.predict(X_test)
print(r2_score(y_test,grid_prediction))
print(mean_absolute_error(y_test,grid_prediction))
```
