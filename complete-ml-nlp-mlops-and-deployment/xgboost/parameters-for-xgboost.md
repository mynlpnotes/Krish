# Parameters for XGBoost

* n\_estimators ([int](https://docs.python.org/3.6/library/functions.html#int)) – Number of gradient boosted trees. Equivalent to number of boosting rounds.
* Max\_Depth
* Learning\_rate – hyper parameter
* Objective – important –
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Objective function is combination of loss + regularization
* Eval\_metric – depends on objective function
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* booster (_Optional\[_[_str_](https://docs.python.org/3.6/library/stdtypes.html#str)_]_) – Specify which booster to use: gbtree, gblinear or dart.
* n\_jobs = number of cores to be used
*   gamma – responsible for controlling number of leaves

    \
