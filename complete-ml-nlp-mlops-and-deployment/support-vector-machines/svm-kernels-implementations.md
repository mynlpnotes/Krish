# SVM kernels implementations

* &#x20;Input data:
*

    <figure><img src="../../.gitbook/assets/image (40).png" alt="" width="250"><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (42).png" alt="" width="193"><figcaption></figcaption></figure>
* We can also create different kernels - for example for power of 2 and then apply linear kernel also
* OR we can directly use kernel = poly

```python
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score
classifier = SVC(kernel="poly")
classifier.fit(X_train, y_train)
y_pred = classifier.predict(X_test)
accuracy_score(y_test, y_pred)

```
