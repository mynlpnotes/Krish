---
hidden: true
---

# ROC - Skip

* Receiver operator curve
* What threshold should we select?
*

    <figure><img src="../../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>
* 0.5 is not the ideal threshold
* 2 different confusion matrix, one for 0.5 threshold and another for 0.7
* Accuracy for 0.5 is 83% and for 0.7 its giving 66%
* But this does not mean 0.5 threshold is better
* We plot TPR and FPR
* ROC is relationship between FPR and TPR
* FPR = 1 – Specificity
* For 0.5, TPR = 0.75, FPR = 0
* For 0.7, TPR = 0.5, FPR = 0
* If we are having a case whether model is accepting more positive values compared to negative, in this case 0.5 will give more positive values
* For medicine trial. We will select threshold as 0.7 or 0.6
*

    <figure><img src="../../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>
* Checking the model with different values of threshold for values of FPR and TPR
* For government scheme we will be looking for high TPR and FPR will be less, so threshold can be 0.5
* If it’s a court case, then threshold should be 0.9
* For every model we can plot ROC curve
* Different models of same or different algo can be compared using AUC
* ROC can be used to select the threshold
*

    <figure><img src="../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>
* For every threshold,m1 is giving better TPR and low FPR than m2, so m1 is better
