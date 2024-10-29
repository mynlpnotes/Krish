# GridSearchCV

* It uses cross validation, if
* grid\_pram = {"criterion":\['gini','entropy'],
* "splitter":\['best','random'],
* "max\_depth" : range(2,40,1),
* "min\_samples\_split":range(2,10 ,1),
* "min\_samples\_leaf":range(1,10,1),
* 'ccp\_alpha':np.random.rand(20)
* }
* grid\_ccp = GridSearchCV(estimator=dt\_model\_ccp,param\_grid=grid\_pram , cv = 10 , n\_jobs=-1)
* grid\_ccp.fit(x1,y1)
* grid\_ccp.best\_params\_
*

    <figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>
*   Same can be done using RandomSearchCV

    \
