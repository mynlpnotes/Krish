# Example

*

    <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
* Lets consider m = 5 and c = 2, then P(x = 2) = 0.99, cost = 0.01
* If m = 21, c = -5, then P(x = 2) = lets suppose it is 1, cost = 0
* If m = 0.3, c = 0.1 , then P(x = 2) = 0.67, cost = 0.33 🡪 in this case, value of m and c needs to be changed a lot
* mnew = mold – learning\_rate \* delta Em
* Taking derivate of cost function for finding delta
*

    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
* If m = 0.3, c = 0.1, x = 6.5, then P(x) = 0.88, calculate logit = 0.86
* If m = 21, c = -5, x = 6.5, then P(x) = 1
* So if use either of this 2 lines, we will be getting same results
* 2nd line is giving more definite out output, in 1st line there was some cost, however in 2nd line there is no cost
* Sigmoid is give the probability, logit gives which region it belongs to, if its +ve then it belongs to +class, if its -ve then it belongs to -ve class
