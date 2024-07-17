# Decision Tree Classifier Implementation

```python
# Load iris data from sklearn dataset
X=pd.DataFrame(iris['data'],columns=['sepal length in cm','sepal width',
'petal length','petal width'])
y=iris['target']

X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.2,random_state=10)

treeclassifier=DecisionTreeClassifier()
treeclassifier.fit(X_train,y_train)

##Visualize the Decision Tree
from sklearn import tree
plt.figure(figsize=(15,10))
tree.plot_tree(treeclassifier,filled=True)
# Gini coeffecient is used
# value = count of different categories

y_pred=treeclassifier.predict(X_test)
cm=confusion_matrix(y_test,y_pred)
print(classification_report(y_test,y_pred))
```

*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
