# Bagging Coding

* from sklearn.ensemble import BaggingClassifier
* bag\_dt = BaggingClassifier(DecisionTreeClassifier() , n\_estimators=100)
* bag\_dt.fit(x\_train  , y\_train)
* bag\_dt.predict(x\_test)
* bag\_dt.base\_estimator\_ 🡪 DecisionTreeClassifier()
* bag\_dt.classes\_ 🡪array(\[3, 4, 5, 6, 7, 8], dtype=int64)
* bag\_dt.estimator\_params 🡪 parameters given for creating DT
* Can also be done for other algo like KNN
* bag\_knn = BaggingClassifier(KNeighborsClassifier(6) , n\_estimators=10)
