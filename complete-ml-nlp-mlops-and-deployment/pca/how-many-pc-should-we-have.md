# How many PC should we have?

* For this we use EVR – explained variance ratio
* If we have PC1 and PC2, then we derive some of the relation with respect to PC1 and some with relation to PC2
* In EVR, we try to calculate how much relation is a single PC able to explain
* (in Linear regression when we say that accuracy is 83% then it means that the line is able to explain 83% of the data
* Remaining 17% can be explained by some other line)
* EVR(PC1) = Distance of PC1 points / ( Distance of PC1 + Distance of PC2)
* \= 50 / (50 + 5)
* \= 0.91
* Then it means EVR(PC1) is able to retain 91% of the data
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* EVR(PC2) = 0.09
* Using PC1 and PC2 we are able to explain 100% of the variance
