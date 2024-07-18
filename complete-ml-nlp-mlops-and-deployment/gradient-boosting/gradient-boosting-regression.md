# Gradient Boosting Regression

*

    <figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Steps:

1. To create a base model

* This should not be biased to any value, it will give a default value
* The output of base model will be 75k (Average of salary)

2. Compute residuals/errors

* R1 = y - ypred

3. Construct a DT considering inputs X and output as residual R1
4. Calculate R2 as residual of this DT
5. For any input what will be predicted output

* Lets say input is 1st record
* Predicted = 75 + (-23) = 52 which is almost the output of 50
* Here the model is performing overfitting
* So we will be calculating predicted as&#x20;
* predicted = 75 + α (-23)
* α is learnable parameter
* if α = 0.1, then ypred = 72.7 then it means the error is very high
* Now we calculate updated ypred

6. Compute R3 as y - updated y pred
7. Again construct DT

* Here input will be X and output will be R3
*

    <figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

8. Again we will calculate ypred, then calculate R4 and construct next DT
9. Final output:

*

    <figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
