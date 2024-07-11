# SVC Implementation

* If data is overlapping then we can try different kernels

```python
from sklearn.svm import SVC
svc=SVC(kernel='linear')

svc.fit(X_train,y_train)
svc.coef_
y_pred=svc.predict(X_test)

from sklearn.metrics import classification_report,confusion_matrix
print(classification_report(y_test,y_pred))
print(confusion_matrix(y_test,y_pred))

# Using RBF kernel
rbf=SVC(kernel='rbf')
rbf.fit(X_train,y_train)

# Using polynomial kernel
polynomial=SVC(kernel='poly')
polynomial.fit(X_train,y_train)

# Using sigmoid kernel
sigmoid=SVC(kernel='sigmoid')
sigmoid.fit(X_train,y_train)

# Hyperparameter tuning
from sklearn.model_selection import GridSearchCV
 
# defining parameter range
param_grid = {'C': [0.1, 1, 10, 100, 1000],
              'gamma': [1, 0.1, 0.01, 0.001, 0.0001],
              'kernel': ['rbf']}

grid=GridSearchCV(SVC(),param_grid=param_grid,refit=True,cv=5,verbose=3)
grid.fit(X_train,y_train)
grid.best_params_
y_pred4=grid.predict(X_test)
print(classification_report(y_test,y_pred4))
print(confusion_matrix(y_test,y_pred4))
```
