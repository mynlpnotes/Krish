# Decision Tree Coding

* Import data
* Pandas profiling
* Checking missing data
* Checking zero/null values
* Remove duplicate rows
* We can work on skewness of attributes
* x\_train , x\_test , y\_train, y\_test = train\_test\_split(x,y,test\_size = .40 , random\_state = 500)
* dt\_model  = DecisionTreeClassifier() 🡪 bydefault criterion is gini
* dt\_model.fit(x\_train,y\_train)
* dt\_model.predict(x\_test)
* dt\_model.score(x\_test, y\_test)
* dt\_en = DecisionTreeClassifier(criterion="entropy") 🡪 Using entropy
* outfile = open('dt\_en\_meta.dot','w')
* tree.export\_graphviz(dt\_en,out\_file=outfile , feature\_names=x.columns)
* This will create a dot file, have entire decision tree generated
*

    <figure><img src="../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>
* set(df.quality) 🡪 get all the possible of target attribute
* data pre-processing is to be done on the data
* Multi collinearity check not needed, as we are splitting the data here
