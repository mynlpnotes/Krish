# Stacking Coding

* Ensemble technique
* In Boosting/Bagging we use same algo for all the estimators
* In stacking we can use multiple algo
* Train different models like knn, svc,
* In stacking we are to do 2 levels of data division
* Data - 100
* Train - 50
* Train – 40 – Use this for training
* Test – 10 –
* Val – 50 – Use this for prediction
* train , val\_train , test , val\_test  = train\_test\_split(x,y,test\_size = .50 , random\_state = 30)
* x\_train , x\_test , y\_train, y\_test = train\_test\_split(train ,test,random\_state = 30 , test\_size = .20)
* predcition\_knn = knn.predict(val\_train)
* prediction\_svc = svc.predict(val\_train)
* Predictions of the base model we will give ad training to the stacking model
* input3 = np.column\_stack((predcition\_knn,prediction\_svc))
* output = val\_test
* pd.DataFrame(input3)
* rf = RandomForestClassifier() 🡪 We can use any model here
* rf.fit(input3,output)
* rf.score(x\_test,y\_test)
* knn\_output = knn.predict(x\_test)
* svc\_output = svc.predict(x\_test)
* output\_stack1 = np.column\_stack ((knn\_output,svc\_output))
* rf.predict(output\_stack1)
* rf.score(output\_stack1 , y\_test)
