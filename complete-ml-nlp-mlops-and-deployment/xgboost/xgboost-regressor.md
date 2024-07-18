# Xgboost Regressor

* &#x20;Similarity weight calculation will change here
* Base model will give us output as 51K (Average of salary)
*

    <figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
* Calculate ypred as 51k
* Compute R1
* Construct DT with X as input and R1 as output
* Calculate similarity weights of root and child's to find which split to use
* Calculate gain
* Similarly we can do for other splits
* Using this we construct DT
* After building this DT, we pass the records and get ypred
*   and calculate R2, using this we would again create 2nd DT and so on

    <figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>
