# Performance Metrics

1. **R squared:**

* SSR is basically square of difference between predicted and actual
* SST is basically square of difference between avg and actual
* SSR supposed to be a small number and SST is supposed to be a bigger number
* Then the result will be a smaller number
* So 1 - smaller number \~\~ 1
* If we get 0.9 then we will say it is 90% accurate
*   The bigger the number, the higher the accuracy

    <figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

2. **Adj. R squared:**

* As the size of house, the price also increases so there is a +ve correlation
* Lets consider now the Rsquared is 0.75
* If we add 1 more feature as no. of bedrooms&#x20;
* And if we can R squared as 0.8
* Now if we add 1 more location , suppose location then R squared might again go up
* Lets add gender also, this is of no significance, but if we add insignificant feature and check the R squared it might increase by a small value
* The problem here is that insignificant features are also increase R squared
* So in adj r squared, it penalizes wrt every insignificant features
*

    <figure><img src="../../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (16) (1) (1).png" alt=""><figcaption></figcaption></figure>
