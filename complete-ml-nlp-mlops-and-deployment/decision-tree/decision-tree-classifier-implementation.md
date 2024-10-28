# Decision Tree Classifier Implementation

* criterion{“gini”, “entropy”, “log\_loss”}, default=”gini”
* max\_depthint, default=None
* min\_samples\_splitint or float, default=2
* min\_samples\_leafint or float, default=1
* max\_featuresint, float or {“auto”, “sqrt”, “log2”}, default=None
* max\_leaf\_nodesint, default=None

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

    <figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
