# Linear Regression - Coding

```python
from pandas_profiling import ProfileReport

ProfileReport(df)
pf = ProfileReport(df)
pf.to_widgets()
pf.to_file('test.html') # to save the report

#Warnings:
#	Here we will be see which variables are highly corelated
#Variables:
#	Here we will get details of all variables, like unique values, 
#       Missing, same details which are available in describe will be seen here 
#       as well
#Interactions:
#	Here we can see scatter for each variable against each other
#	We will be able to see whether the independent variables are correlated 
#       with dependent variable
#	Similarly we will also be able to see for multicollinearity among 
#       feature columns
#Correlations:
#	Pearson, spearman etc will be shown all the variables
#This html page we can also show it to the user
from sklearn.linear_model import LinearRegression
linear = LinearRegression()

linear.fit(x,y) # Need to pass 2d array
linear.intercept_
linear.coef_

file = 'linear_reg.sav' # sav is byte code format
pickle.dump(linear,open(file,'wb'))
saved_model = pickle.load(open(file,'rb'))

#Pickle is a serializable file format
linear.score(x,y) #🡪 To get accuracy – R2
```

* Bias means error and variance means dispersion
* <mark style="color:purple;background-color:purple;">**By default linear regression is high bias low variance model**</mark>
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**The difference between line and actual points will always be there, so there will be high bias**</mark>
* <mark style="color:purple;background-color:purple;">**Even if we add more data the line wont change much, that means the variance of the line will be very less and that’s why its called as a low variance model**</mark>
