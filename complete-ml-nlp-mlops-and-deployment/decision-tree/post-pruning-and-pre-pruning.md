# Post Pruning & Pre Pruning

* If we use by default parameter then the algorithm will keep splitting till it get all the leaf node
* This will result in overfitting
* To reduce overfitting we can use

1. Post pruning:&#x20;

* We will complete entire DT&#x20;
* Prune w.r.t depth
* Can be done for smaller dataset

2. Pre pruning:&#x20;

* Don't construct entire decision tree
* We can prune using hyper parameters like min\_samples, max\_depth etc
