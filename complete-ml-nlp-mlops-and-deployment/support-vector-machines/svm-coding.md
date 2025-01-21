# SVM Coding

* from sklearn.svm import SVC
* svc= SVC()
* svc.fit(x\_train,y\_train)
* svc.score(x\_test,y\_test)
* param ={"kernel":\['linear', 'poly', 'rbf', 'sigmoid' ], 'C':\[.1,.4 , .6 , 1,2,3,100,200,500],       &#x20;
* 'gamma':\[.001,.1,.4,.004,.003]   }
* Precomputed means custom function
* If we choose kernel as poly then only it will consider degree parameter, degree is ignored by all other kernels
* Gamma is used for rbf, poly, sigmoid, default value is 1 / ( x\_features \* X.var())
* Kernel is responsible for creating the n+1 dimension, but the new dimension should not be too big or too small, otherwise it will cause issue in separation
* svm\_grid = GridSearchCV(svc , param\_grid=param , verbose=3 )
* svm\_grid.fit(x\_train,y\_train)
* svm\_grid.best\_params\_
