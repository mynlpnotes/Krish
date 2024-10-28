# Gradient Boosted Tree

* Boosting technique
* Can be used for regression as well as classification
* Find total error, we reduce error
* But here the approach we use to reduce the error is gradient (derivative)
* Wnew = Wold +- learning\_rate \* (delta Ew)
*   Residual = actual\_label – predicted\_result

    \-          The predicted result is the average of each and every decision maker

    \-          We then find partial derivate of error with the parameter which we are trying to optimize

    \-          New\_value = old\_value + learning\_rate \* residual

    Once residual stops decreasing we will stop the process
