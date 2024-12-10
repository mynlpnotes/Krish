# Residual

* <mark style="color:purple;background-color:purple;">**Y – Ypred**</mark>
* Y – (mx + c)
* Denoted as r
* <mark style="color:purple;background-color:purple;">**r2 will be independent of the direction (called residual square)**</mark>
* Our aim is to find a point where residuals are supposed to be 0
* A point where derivative of e wrt m should be 0
* And derivative of e wrt c should be 0
* Residuals are nothing but errors
* <mark style="color:purple;background-color:purple;">**Goal is to find derivate of residual wrt m and wrt c where its tending to 0, that is the point which we want**</mark>
*

    <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Delta Ec is a value of E where it will be 0
* <mark style="color:purple;background-color:purple;">**0.001 is good learning rate (Range 10 to 0.00001)**</mark>
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>


* Here for calculating Ec and Em we have used only 3rd point, but in actual summation of all the values is to be taken
* <mark style="color:purple;background-color:purple;">**Find delta Ec and Em**</mark>
* <mark style="color:purple;background-color:purple;">**Then find New m and c**</mark>
* <mark style="color:purple;background-color:purple;">**Find error again**</mark>
* <mark style="color:purple;background-color:purple;">**Using new values again find Ec and Em**</mark>
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
