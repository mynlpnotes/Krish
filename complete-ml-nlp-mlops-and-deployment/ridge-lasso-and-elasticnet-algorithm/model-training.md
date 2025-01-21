# Model Training

```python
# Linear Regression
linreg=LinearRegression()
linreg.fit(X_train_scaled,y_train)
y_pred=linreg.predict(X_test_scaled)
mae=mean_absolute_error(y_test,y_pred)
score=r2_score(y_test,y_pred)
print("Mean absolute error", mae)
print("R2 Score", score)
plt.scatter(y_test,y_pred)

# Lasso Regression
lasso=Lasso()
lasso.fit(X_train_scaled,y_train)

# Ridge Regression
ridge=Ridge()
ridge.fit(X_train_scaled,y_train)

# ElasticNet
elastic=ElasticNet()
```
