# SGD with momentum

* Using this we want to smoothen the curve so that noise is reduce and convergence happens fast
* Below are the formula to update weights and bias
*   This formulas can also be written as a time series

    <figure><img src="../../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>
* For this we need to know exponential weighted average using this smoothening will happen
* Lets say we have the below time and values
* If we join all the values in the plot, it wont be smooth
* Vt1 = a1
* Vt2 will be calculated using the new formula
* Here we want previous value to control more, so we put β value more
* This will smoothen the curve
*

    <figure><img src="../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>
