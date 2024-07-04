# Hyper Parameter Tuning

* &#x20;LassoCV itterative fitting along a regularization path
* It will try to play with all the parameters and try to select the most suitable parameters
* There is a parameter like n\_aplha = 100, that means 100 different alpha values will be tried

```python
# LassoCV will give us alpha value
lassocv=LassoCV(cv=5)
lassocv.fit(X_train_scaled,y_train)
lassocv.alpha_ # Alpha value
# Can be used for prediction also
y_pred=lassocv.predict(X_test_scaled)
plt.scatter(y_test,y_pred)
mae=mean_absolute_error(y_test,y_pred)
score=r2_score(y_test,y_pred)
print("Mean absolute error", mae)
print("R2 Score", score)

# Similarly RidgeCV can also be used

# Similarly ElasticNet also
```
