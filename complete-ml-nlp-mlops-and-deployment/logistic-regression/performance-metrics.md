# Performance Metrics

* &#x20;In linear regression we used r2 and adj.r2 to understand model performance
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;For binary classification, confusion matrix will be 2X2
* TP and TN are our correct results
* Accuracy = (TP + TN ) /  (TP + FP + TN + FN)
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In case of imbalanced dataset, we cannot use accuracy, as if our model predicts 1 always then also it will be 90% accurate
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Precision means out of all the predicted results, how many are actually correct
*   Recall means out of all the actual positive instances, how many did the model correctly identify

    <figure><img src="../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;Here we want to reduce FP, so we want to use precision
*

    <figure><img src="../../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Here we want to use recall
*

    <figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;β>1 gives more weight to recall.
* β<1\ gives more weight to precision.
* F2 score is preferred in scenarios where recall is more critical than precision
*

    <figure><img src="../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>
