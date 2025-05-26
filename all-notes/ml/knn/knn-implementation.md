# KNN Implementation

* Parameters:
* n = no. of neighbours
* weights: unifrom - All neighbors have equal weights, distance - the neighbors which are closer will have more weight
* algorith - kdtree, ball tree, auto - based on the input features
* p = algorithm to be used for distance calculation

```python
from sklearn.neighbors import KNeighborsClassifier
classifier=KNeighborsClassifier(n_neighbors=5,algorithm='auto')
classifier.fit(X_train,y_train)

y_pred=classifier.predict(X_test)
print(confusion_matrix(y_pred,y_test))
print(accuracy_score(y_pred,y_test))
print(classification_report(y_pred,y_test))


regressor=KNeighborsRegressor(n_neighbors=6,algorithm='auto')
regressor.fit(X_train,y_train)
y_pred=regressor.predict(X_test)
print(r2_score(y_test,y_pred))
print(mean_absolute_error(y_test,y_pred))
print(mean_squared_error(y_test,y_pred))
```
