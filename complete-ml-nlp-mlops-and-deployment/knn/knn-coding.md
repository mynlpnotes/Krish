# KNN Coding

* knn1 = KNeighborsClassifier()
* knn1.fit(x\_train,y\_train)
* knn.score(x\_test, y\_test)
* pram  = {
* 'n\_neighbors':\[3,5,7,9,12,13,15,17,21],
* 'algorithm' : \['auto', 'ball\_tree', 'kd\_tree', 'brute'],'leaf\_size' : \[10 , 15 , 20 , 25 , 30 , 35 , 45 , 50 ],
* 'p' : \[1,2],
* 'weights' : \['uniform', 'distance']
* }
* grid\_cv = GridSearchCV(knn,param\_grid=pram )
* grid\_cv.fit(x\_train, y\_train)
* grid\_cv.best\_params\_
* it is possible the size of the pickle file is more than the dataset itself
* As we change the dataset/parameters for model, the size of the model changes\
