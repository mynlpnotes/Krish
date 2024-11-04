# Overview

* One of the pre-processing step
* Can be used for dimension reduction
* Need for dimension reduction:
* We have x1 x2 ….. x100     y
* If we pass such data for training, then time complexity for training will increase
* Difficult to generalize
* This is known as curse of dimensionality
* All the time all the features are not going to contribute
* Hard to find out shape of data
* It does not mean removing columns
* We are trying to convert data to some other axis is such a way that it will be able to retain original meaning of the data
* This are the datapoints given
* X1 X2
* 2   2
* \-1  2
* \-2  -2
*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
* Can this be represented using just 1 axis?
* If we project the points on x1, we wont be able to form relation between x1 and x2
* On some new axis we can represent both x1 and x2
* Then this line is going to represent relation of both
* PCA says its possible to convert 1 of the axis into another axis
* It is possible to derive 1 axis as part of another axis
