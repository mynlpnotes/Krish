# DT Split for Numerical Features

* Sort the feature value
* We create many decision tree
* In 1st tree we will take threshold as 1st value
* In 2nd tree we will take 2nd value as threshold
* Like this we will create different DT
* We calculate information gain
* Whichever split is having best information gain, that will be selected as root node
* If we have million of records, then time complexity is very high
*

    <figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>
*
