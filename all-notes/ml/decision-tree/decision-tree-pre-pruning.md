# Decision Tree Pre pruning

```python
param={
    'criterion':['gini','entropy', 'log_loss'],
    'splitter':['best','random'],
    'max_depth':[1,2,3,4,5],
    'max_features':['auto','sqrt','log2']
}

treemodel=DecisionTreeClassifier()
grid=GridSearchCV(treeclassifier,param_grid=param,cv=5,scoring='accuracy')

grid.fit(X_train,y_train)
grid.best_params_
grid.best_score_
y_pred=grid.predict(X_test)
```
