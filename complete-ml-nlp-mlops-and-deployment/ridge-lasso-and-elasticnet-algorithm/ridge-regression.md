# Ridge Regression

* Used to reduce overfitting
* Also called L2 regularization
* &#x20;Cost function is different here
* If line is passing through all the training data points, then our cost function will become 0
* In order to ensure it never becomes 0, so we add 2 parameters lambda and summation of slope square
* Lambda is a hyper parameter
* We penalize the cost function by adding this term
* So model will try to find another best fit line which will reduce cost function
* <mark style="color:purple;background-color:purple;">**What is the relation between lambda and slope2???**</mark>
* If lamda = 0 then we get gradient descent which is white
* if we make lambda = 10, then we will get red gradient descent, here we will see our global minima has shifted, Also our theta value has decreased
* if we increase lambda again, then we will get another line where global minima will gain shifted
* But theta will never be 0
* If lambda is increasing then slope is decreasing
* If we have multi linear regression with 3 coefficients
* If we apply ridge regression then the coefficients will reduce
* If for a small increase in coefficients there is a large change in output, then we will say they are highly correlated
* So if we increase lambda then for small change in coefficients then output wont change much
* Since the coefficients are small so by changing it there wont be much change in best fit line
* The variables which are not correlated to output, it will decrease its value also, so that the unrelated variables wont have much impact on output
*

    <figure><img src="../../.gitbook/assets/image (36) (1).png" alt=""><figcaption></figcaption></figure>





