# Pruning

* path = dt\_model1.cost\_complexity\_pruning\_path(x1,y1)
*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
* ccp\_apha - Complexity parameter used for Minimal Cost-Complexity Pruning. The subtree with the largest cost complexity that is smaller than ccp\_alpha will be chosen. By default, no pruning is performed.
* ccp\_alpha = path.ccp\_alphas
* We can plot ccp\_alphas vs accuracy on training and test data
* If the cost of some branches is more than the threshold, then we will cut that branch
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
* train\_score = \[i.score(x1,y1) for i in dt\_modle2]
* test\_score = \[i.score(x\_test ,y\_test) for i in dt\_modle2]
*

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
* CCP value to be considered is between 0.01 and 0.02
* Hyper tuning of ccp value is one of the solution for overfitting , using post pruning
* dt\_model\_ccp = DecisionTreeClassifier(random\_state=0 , ccp\_alpha=.014)
* After pruning the accuracy is about 58%
* confusion\_matrix(y\_train,pred)
