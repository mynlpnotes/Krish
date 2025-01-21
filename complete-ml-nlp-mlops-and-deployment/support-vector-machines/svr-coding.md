# SVR Coding

* from sklearn.svm import SVR
* svr = SVR()
* svr.fit(x\_train, y\_train)
* from sklearn.metrics import r2\_score
* r2\_score(y\_test ,  svr.predict(x\_test))
* svr.predict(x\_test)
* svr.score(x\_test,y\_test)

Score gives r2 for regression and accuracy for classification algorithm
