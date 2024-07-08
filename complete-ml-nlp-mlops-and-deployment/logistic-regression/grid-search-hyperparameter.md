# Grid Search Hyperparameter

{% embed url="https://github.com/krishnaik06/Complete-Data-Science-With-Machine-Learning-And-NLP-2024/blob/main/6-Logistic%20Regression/Logistic%20Practicals/Logistic%20Regression%20Implementation.ipynb" %}

```python
model=LogisticRegression()
penalty=['l1', 'l2', 'elasticnet']
c_values=[100,10,1.0,0.1,0.01]
solver=['newton-cg', 'lbfgs', 'liblinear', 'sag', 'saga']

params=dict(penalty=penalty,C=c_values,solver=solver)

from sklearn.model_selection import StratifiedKFold
cv=StratifiedKFold()

from sklearn.model_selection import GridSearchCV
grid=GridSearchCV(estimator=model,param_grid=params,scoring='accuracy',cv=cv,
n_jobs=-1)

grid.fit(X_train,y_train)
grid.best_params_ # {'C': 0.01, 'penalty': 'l1', 'solver': 'saga'}
grid.best_score_ # 0.9242857142857142

y_pred=grid.predict(X_test)
score=accuracy_score(y_pred,y_test)
print(score)
print(classification_report(y_pred,y_test))
print(confusion_matrix(y_pred,y_test))
```
