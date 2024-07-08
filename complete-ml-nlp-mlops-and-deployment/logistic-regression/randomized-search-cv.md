# Randomized Search CV

{% embed url="https://github.com/krishnaik06/Complete-Data-Science-With-Machine-Learning-And-NLP-2024/blob/main/6-Logistic%20Regression/Logistic%20Practicals/Logistic%20Regression%20Implementation.ipynb" %}

* Grid search takes all the combinations so it takes time
* Randomized search takes random parameters

```python
randomcv=RandomizedSearchCV(estimator=model,param_distributions=params,
cv=5,scoring='accuracy')
randomcv.fit(X_train,y_train)
randomcv.best_score_
randomcv.best_params_
y_pred=randomcv.predict(X_test)
```

