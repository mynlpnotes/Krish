# Practical - Polynomial Regression

* &#x20;
*

```python
X = 6 * np.random.rand(100, 1) - 3
y =0.5 * X**2 + 1.5*X + 2 + np.random.randn(100, 1)
# quadratic equation used- y=0.5x^2+1.5x+2+outliers
plt.scatter(X,y,color='g')

X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.2,random_state=42)

regression_1=LinearRegression()
regression_1.fit(X_train,y_train)
score=r2_score(y_test,regression_1.predict(X_test)) # 0.62

# Apply polynomial features
poly=PolynomialFeatures(degree=2,include_bias=True)
X_train_poly=poly.fit_transform(X_train)
X_test_poly=poly.transform(X_test)

regression = LinearRegression()
regression.fit(X_train_poly, y_train)
y_pred = regression.predict(X_test_poly)
score=r2_score(y_test,y_pred) # 0.93

plt.scatter(X_train,regression.predict(X_train_poly))
plt.scatter(X_train,y_train)

print(regression.coef_) # [[0.         1.5819644  0.50905021]]
print(regression.intercept_) # [1.84676477]
```

*

    <figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption><p>Dataset</p></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption><p>Best fit line with degree = 2</p></figcaption></figure>
