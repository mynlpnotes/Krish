# XGBoost Classification Indepth Intuition

* XGboost can also run on GPU
* Construct a base model - This will give equal probability for all the outputs
* Calculate R1 as difference between y - ypred
* Construct a DT, input will be salary and credit and output will be R1
* Calculate similarity weight and gain
* Lets say we split using salary
*

    <figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
* &#x20;Calculate similarity weight for child and root
* Calculate gain = similarity weight of childs - similarity weight of root
*   For next split again we do the same thing

    <figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
* For any new test data, we will be passing it through log of odds, which will be 0 for base model
* Output of DT will be similarity weight \* alpha
* We apply a sigmoid activation function to the sum of outputs
* Value which will come after sigmoid will be the ypred for the 1st record
*

    <figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>
* Compute R2
* Construct next DT using X and output as R2
* This will go on
*   Final prediction function will be calculated as

    <figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
* We keep splitting till we get any similarity weight which is less than P(1-P) -- This is the denominator value of similarity weight -- this is also known as cover value
