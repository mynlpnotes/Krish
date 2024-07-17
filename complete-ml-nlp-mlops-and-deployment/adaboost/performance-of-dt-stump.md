# Performance of DT stump

* Now we will be doing 2 operations - Sum of total errors and performance of stump
* We assign some sample weights
* Initially we assign equal records to all the records
* Here 1 Y is wrongly classified, so it is our error
* So sum of total error = 1/7
* Calculate performance of stump = 1/2 \* ln \[(1 - TE) / TE] = 0.896
* This 0.869 will be the weight of the model
* Pass this wrong predicted records to the next DT stump
*

    <figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>
