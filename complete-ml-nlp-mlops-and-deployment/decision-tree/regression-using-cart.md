# Regression Using CART

| X1  | X2  | X3  | Y    |
| --- | --- | --- | ---- |
| 1   | 2   | 1   | 3    |
| 2.4 | 5.8 | 6   | 10   |
| 2.9 | 6.1 | 7.2 | 12.8 |
| 5.8 | 2.8 | 9.6 | 13.9 |
| 7.2 | 7.8 | 8.9 | 14.8 |

* Divide X1 at 2.5, X2 at 6 , X3 at 6
* Suppose we build tree using
*

    <figure><img src="../../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>
* How will be get continuous output?
* Find summation of  (y - ypred )2  for all the records, ypred will be average, keep residuals as less as possible
*

    | X1 | X2 | Y  |
    | -- | -- | -- |
    | 1  | 10 | 5  |
    | 2  | 20 | 10 |
    | 3  | 30 | 15 |
    | 4  | 40 | 25 |
    | 5  | 50 | 25 |
    | 6  | 60 | 30 |
* Thresholds as 3,30 and 15
*

    <figure><img src="../../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure>
* Similarly we can build another decision tree using another threshold
* Since we are using threshold, same concept of gini and information gain will be replicable
