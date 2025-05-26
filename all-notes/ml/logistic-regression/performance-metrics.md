# Performance Metrics

* &#x20;In linear regression we used r2 and adj.r2 to understand model performance
*

    <figure><img src="../../../.gitbook/assets/image (371).png" alt=""><figcaption></figcaption></figure>
* For binary classification, confusion matrix will be 2X2
* TP and TN are our correct results
* <mark style="color:purple;background-color:purple;">**Accuracy = (TP + TN ) /  (TP + FP + TN + FN)**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (372).png" alt=""><figcaption></figcaption></figure>
* In case of imbalanced dataset, we cannot use accuracy, as if our model predicts 1 always then also it will be 90% accurate
*

    <figure><img src="../../../.gitbook/assets/image (373).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Precision means out of all the predicted results, how many are actually correct**</mark>
*   <mark style="color:purple;background-color:purple;">**Recall means out of all the actual positive instances, how many did the model correctly identify**</mark>

    <figure><img src="../../../.gitbook/assets/image (374).png" alt=""><figcaption></figcaption></figure>
* &#x20;Here we want to reduce FP, so we want to use precision
*

    <figure><img src="../../../.gitbook/assets/image (375).png" alt=""><figcaption></figcaption></figure>
* Here we want to use recall
*

    <figure><img src="../../../.gitbook/assets/image (376).png" alt=""><figcaption></figcaption></figure>
* &#x20;β>1 gives more weight to recall.
* β<1 gives more weight to precision.
* <mark style="color:purple;background-color:purple;">**F1 score is used when recall and precision both are equally important**</mark>
* <mark style="color:purple;background-color:purple;">**F2 score is preferred in scenarios where recall is more critical than precision**</mark>
* $$[ F_\beta = \frac{(1 + \beta^2) \times \text{Precision} \times \text{Recall}}{\beta^2 \times \text{Precision} + \text{Recall}} ]$$ <mark style="color:purple;background-color:purple;">-> -> -> Correct equation</mark>
*

    <figure><img src="../../../.gitbook/assets/image (377).png" alt=""><figcaption></figcaption></figure>
