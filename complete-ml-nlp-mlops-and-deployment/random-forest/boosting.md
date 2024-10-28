# Boosting

* Boost the decision made by previous decision maker
* Weak classifier is slightly better than a random guess
* N 🡪 Samples
* m 🡪 No. of models
* Decision to be made (Y,N) or (1,-1)
* N will be large and we are not sure which records will give us proper relationship

1. Initally we will be giving a weightage of 1/N to all the records
2. 1st model, Gm(X)
3. Calculate errorm =  ( summation (wi \* Instance (y != ypred))) / N
4. Compute alpha = ½ log(1 – errorm) / errorm
5. Reassign wi = wi \* exp(apha . I(y!= ypred))
6. Normalize, so that summation of all the weights should be 1
7. Construct the next tree with the new weights
8. The final results

*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
