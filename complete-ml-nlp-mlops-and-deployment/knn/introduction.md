# Introduction

* Lazy learning algorithm
* Model size will increase as the number of training instances increase
* It will do calculations at run time
* If datasize is huge, then it should not be used
* For deciding what should be the label for a new instance, we can find it by calculating similarity with the existing instances
* Find the top 3 minimum distance
* Find the corresponding class for those 3 instances
* Find P(Class 1) and P(Class 2), then take the one having highest probability as the label for the new instance
* K is a hyper parameter
* No training as such
* If the data is mix of categorical + numerical then convert all the categorical data into vector space
