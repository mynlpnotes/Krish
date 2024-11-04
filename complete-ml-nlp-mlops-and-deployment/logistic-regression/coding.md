# Coding

* Do pandas profiling
* Interactions – As we are not working on linear data so we don’t need to worry about scatter plot
* df\['BMI'] = df\['BMI'].replace(0 , df\['BMI'].mean()) 🡪 Replace 0 with mean
* if data is skewed its better to replace with mean rather than median or mode
* After replacing with 0, its histogram in pandas profiling it was almost normally distributed
* Skewness can be coz of outliers
* Plot boxplot to see the outliers
* fig ,ax  = plt.subplots(figsize = (20,20))
* sns.boxplot(data = df , ax = ax)
*

    <figure><img src="../../.gitbook/assets/image (17) (1) (1).png" alt=""><figcaption></figcaption></figure>
* q = df\['Pregnancies'].quantile(.98)
* df\_new = df\[df\['Pregnancies'] < q]
* Keep 1 or 2 percent only otherwise will lose lot of data
* Do this for all the columns having outliers
* If we delete one columns, others can be affected as well , as the entire record is deleted
* After doing this we can again check histogram in pandas profiling if skewness has reduced
* We can also remove outliers using
*

    <figure><img src="../../.gitbook/assets/image (18) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We can also use log transformation
* Since the columns are in very different ranges, we will standardize this
*

    <figure><img src="../../.gitbook/assets/image (19) (1) (1).png" alt=""><figcaption></figcaption></figure>
* After standardize, we will again boxplot and then check that all are on the same scale
* If even after removing outliers, there are still outliers then need to keep them

**Check multicollinearity:**

* Check VIF, if its above 10 for X
* Train test split the data
* logr\_liblinear = LogisticRegression(verbose=1,solver='liblinear') 🡪
* verbose to display information
* l1\_ratio – for regularization
* n\_jobs number of cpu cores to be used, -1 means all processors
* Incase of multiclass it used OvR
* default solver is lbfgs
* elastic solver is supported by saga solver only
* google 🡪 logistic regression sklearn 🡪 to see the entire documentation
* Solver – algorithm to use for optimization
*

    <figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
* For multi class classification, we use categorical cross entropy loss
* logr\_liblinear.fit(x\_train,y\_train )
* logr.predict\_proba(\[x\_test\[1]]) 🡪 array(\[\[0.91450958, 0.08549042]])
* logr.predict(\[x\_test\[1]]) 🡪 array(\[0], dtype=int64)
* logr.predict\_log\_proba(\[x\_test\[1]]) 🡪 array(\[\[-0.08742167, -2.48040456]])
* confusion\_matrix(y\_test,y\_pred\_default)
* def model\_eval(y\_true,y\_pred):
  * tn, fp, fn, tp = confusion\_matrix(y\_test,y\_pred).ravel()
  * accuracy=(tp+tn)/(tp+tn+fp+fn)
  * precision=tp/(tp+fp)
  * recall=tp/(tp+fn)
  * specificity=tn/(fp+tn)
  * F1\_Score = 2\*(recall \* precision) / (recall + precision)
  * result={"Accuracy":accuracy,"Precision":precision,"Recall":recall,'Specficity':specificity,'F1':F1\_Score}
  * return result
* model\_eval(y\_test,y\_pred\_liblinear)
* Even if we used 2 different solver, we got the same results
* auc = roc\_auc\_score(y\_test,y\_pred\_liblinear) 🡪 to get AUC
* fpr, tpr, thresholds = roc\_curve(y\_test,y\_pred\_liblinear)
*

    <figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
