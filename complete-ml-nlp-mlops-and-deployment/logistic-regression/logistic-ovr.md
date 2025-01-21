# Logistic OVR

* <mark style="color:purple;background-color:purple;">**We just need to pass multi\_class = ovr in parameter**</mark>

```python
from sklearn.linear_model import LogisticRegression
logistic=LogisticRegression(multi_class='ovr')
logistic.fit(X_train,y_train)
y_pred=logistic.predict(X_test)
```

