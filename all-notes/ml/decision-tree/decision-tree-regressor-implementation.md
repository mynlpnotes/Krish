# Decision Tree Regressor Implementation

* We have use negative mean squared error for scoring
* criterion{“squared\_error”, “friedman\_mse”, “absolute\_error”, “poisson”}, default=”squared\_error”
* max\_depthint, default=None
* min\_samples\_splitint or float, default=2
* min\_samples\_leafint or float, default=1
* max\_featuresint, float or {“auto”, “sqrt”, “log2”}, default=None

```python
# from sklean load diabetes dataset
# all are numeric features here
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.3,random_state=10)

## correlation
X_train.corr()
sns.heatmap(X_train.corr(),annot=True)

regressor=DecisionTreeRegressor()
regressor.fit(X_train,y_train)


param={
    'criterion':['squared_error','friedman_mse','absolute_error'],
    'splitter':['best','random'],
    'max_depth':[1,2,3,4,5,10,15,20,25],
    'max_features':['auto','sqrt','log2']
}

regressor=DecisionTreeRegressor()
grid=GridSearchCV(regressor,param_grid=param,cv=5,scoring='neg_mean_squared_error')
grid.fit(X_train,y_train)
```
