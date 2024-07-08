# Logistic Imbalanced Data

* We will be making use of class weights of logistic regression
* Class weights will help to assign more importance to categories having less records

```python
class_weight=[{0:w,1:y} for w in [1,10,50,100] for y in [1,10,50,100]]
# Output:
#[{0: 1, 1: 1}, {0: 1, 1: 10}, {0: 1, 1: 50}, {0: 1, 1: 100},
# {0: 10, 1: 1}, {0: 10, 1: 10}, {0: 10, 1: 50}, {0: 10, 1: 100},
# {0: 50, 1: 1}, {0: 50, 1: 10}, {0: 50, 1: 50}, {0: 50, 1: 100},
# {0: 100, 1: 1}, {0: 100, 1: 10}, {0: 100, 1: 50}, {0: 100, 1: 100}]
# All the different combinations of importance for 0 and 1

params=dict(penalty=penalty,C=c_values,solver=solver,class_weight=class_weight)

cv=StratifiedKFold()
grid=GridSearchCV(estimator=model,param_grid=params,scoring='accuracy',cv=cv)

grid.fit(X_train,y_train)
```
