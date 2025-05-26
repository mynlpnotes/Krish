# Pre pruning and post pruning

* Performance on unseen data is less - Overfitting
* This can be coz of wrong branches or threshold
* Post pruning is also called back pruning
* In post pruning, we 1st build the tree and then identify which branches are not contributing or coz of which underfitting or overfitting is happening
* Using cross validation if we can find out non performing branch, if the branch is removed then residual reduces then we remove the branch
* Pre pruning is know as forward pruning
* We try to stop tree from generating non significant tree
* By specifying depth of tree
* Here we use regularization we use for pruning
