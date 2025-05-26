# Logistic Regression Implementation

{% embed url="https://github.com/krishnaik06/Complete-Data-Science-With-Machine-Learning-And-NLP-2024/blob/main/6-Logistic%20Regression/Logistic%20Practicals/Logistic%20Regression%20Implementation.ipynb" %}

* We use predic\_proba to understand what is the probability of the value in the category
*

```python
# Make your own dataset
from sklearn.datasets import make_classification
## create the dataset
X, y = make_classification(n_samples=1000, n_features=10, n_classes=2, 
random_state=15)

X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.30,random_state=42)

from sklearn.linear_model import LogisticRegression
logistic=LogisticRegression()
logistic.fit(X_train,y_train)
y_pred=logistic.predict(X_test)
print(y_pred

from sklearn.metrics import accuracy_score,classification_report,confusion_matrix
score=accuracy_score(y_pred,y_test)
print(score)
print(classification_report(y_pred,y_test))
print(confusion_matrix(y_pred,y_test))
# Output:
#0.9166666666666666
#              precision    recall  f1-score   support
#
#           0       0.93      0.91      0.92       160
#           1       0.90      0.92      0.91       140
#
#    accuracy                           0.92       300
#   macro avg       0.92      0.92      0.92       300
#weighted avg       0.92      0.92      0.92       300
#
#[[146  14]
# [ 11 129]]


```
