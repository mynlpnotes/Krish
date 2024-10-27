# Residual

* Y – Ypred
* Y – (mx + c)
* Denoted as r
* r2 will be independent of the direction (called residual square)
* Our aim is to find a point where residuals are supposed to be 0
* A point where derivative of e wrt m should be 0
* And derivative of e wrt c should be 0
* Residuals are nothing but errors
* Goal is to find derivate of residual wrt m and wrt c where its tending to 0, that is the point which we want
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* Delta Ec is a value of E where it will be 0
* 0.001 is good learning rate (Range 10 to 0.00001)
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>


* Here for calculating Ec and Em we have used only 3rd point, but in actual summation of all the values is to be taken
* Find delta Ec and Em
* Then find New m and c
* Find error again
* Using new values again find Ec and Em
*

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
