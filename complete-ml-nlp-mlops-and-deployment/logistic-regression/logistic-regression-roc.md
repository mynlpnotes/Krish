# Logistic Regression ROC

* When we use model.predict we get 0 or 1 as result
* Internally it uses threshold as 0.5 if probability is less then it will be 0 or 1
* As per the domain this threshold can change
* For roc we will be passing actual y and the predicted prob of y
* ROC gives us FPR and TPR
* <mark style="color:purple;background-color:purple;">**If we plot TPR on y axis and FPR on x-axis then we get ROC curve**</mark>
* The area under ROC is known as AUROC
* The greater the area, better the AUROC
* We need to select threshold for which we will be getting high TPR and low FPR
* Domain expert will tell the TPR required and then accordingly we will be keeping threshold ensuring that FPR is not too high

```python
# Dummy model will always give output as 0
dummy_model_prob = [0 for _ in range(len(y_test))]

model_prob=model.predict_proba(X_test)
# array([[8.16436799e-02, 9.18356320e-01],[1.13414988e-01, 8.86585012e-01],....])

# We will be focusing on positive outcome here
model_prob=model_prob[:,1]

dummy_model_auc=roc_auc_score(y_test,dummy_model_prob) # 0.5
model_auc=roc_auc_score(y_test,model_prob)             # 0.91

dummy_fpr, dummy_tpr, _ = roc_curve(y_test, dummy_model_prob)
model_fpr, model_tpr, thresholds = roc_curve(y_test, model_prob)




```

*

    <figure><img src="../../.gitbook/assets/image (21) (1).png" alt=""><figcaption></figcaption></figure>
