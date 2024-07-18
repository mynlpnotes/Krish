# Decision Tree Regression

* We cannot use entropy, gini, information gain in DT regressor
*

    <figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
* We will start with split of exp of 2 and then with 2.5
* Here we will be using variance reduction for selecting the node which is to be selected for split
* Find average at root node and child node
* Find variance at root node
* Find variance for child nodes
* Calculate variance reduction for this split
* Variance reduction = Var(root) - ∑ w var(child) -> w here is weighted average
* Similarly do this for all the splits
* Select the split which is having more variance reduction
* For the new test data, we will parse the tree and it the output will be the average of all the values of the leaf node
*

    <figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
