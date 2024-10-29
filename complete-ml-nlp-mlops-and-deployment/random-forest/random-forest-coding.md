# Random Forest Coding

* from sklearn.ensemble import RandomForestClassifier
* rf = RandomForestClassifier(n\_estimators=5)
* rf.fit(x\_train, y\_train)
* rf.score(x\_test,y\_test)
* All the tree use different subsample
* We can also visualize the DT individually generated in RF
* tree.plot\_tree(rf.estimators\_\[1],filled=True)
* How they are using which subsamples for which tree, we won’t be able to know
* Hyper parameter tuning can be done in same manner as DT
* grid\_pram = {"n\_estimators" : \[5,10 , 50 , 100 , 120 , 150],
* 'criterion' :\['gini' ,'entropy'],
* 'max\_depth' :range(10),
* 'min\_samples\_leaf' :range(10)
* }
* rf = RandomForestClassifier(n\_estimators=5)
* grid\_serach\_rf.fit(x\_train,y\_train)
* grid\_serach\_rf.best\_params\_



**After hyper parameter tuning we cannot guarantee better accuracy, but it can surely increase stability**
