# Can Linear Regression Solve Classifier Problem

* Output variable will be categorical
* Let us plot this data
* If we want to solve this with linear problem, then the aim of linear regression is to find the best fit line
* So here for 5 hours we will say that he will fail as its value will be less than 0.5
* If we have an outlier, where a person studies for 12 hours and pass
* Now the line will get shifted because of the outlier
* Now if we plot for 5 hours then still he will be failing
* <mark style="color:purple;background-color:purple;">**We cannot use linear regression as due to some outlier our best fit line changes**</mark>
* <mark style="color:purple;background-color:purple;">**Also we can also have value greater than 1 and less than 0 also**</mark>
* <mark style="color:purple;background-color:purple;">**But we want a value between 0 and 1**</mark>
* We want to squash our line between 0 and 1, and this can be done only using logistic regression
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (39) (1).png" alt=""><figcaption></figcaption></figure>
*
