# Introduction

* Divides the first
* Then at the last level we get the class
* Can also work for regression
* If the data is separable then we can use logistic regression, but if the data is very irregular then in such scenario we can go for decision tree
* A tree will have multiple branches
* Final node will give output class
* Good at handling missing value
* Example:

| Class | Gender | Stay in Hostel |
| ----- | ------ | -------------- |
| 9     | M      | Y              |
| 10    | F      | N              |
| 8     | F      | Y              |
| 8     | F      | N              |
| 9     | M      | Y              |
| 10    | M      | N              |
| 11    | F      | Y              |
| 11    | M      | Y              |
| 8     | F      | Y              |
| 9     | M      | N              |
| 11    | M      | N              |
| 11    | M      | Y              |
| 10    | F      | N              |
| 10    | M      | Y              |
| 8     | F      | ?              |

* Decision tree can be built for the same in multiple ways

1. We can 1st start with Gender and then take class and then output
2. We can also start with Class and then take gender and then output

* Which node should be select node? Parent node? Which node to be select 2nd?
* Information gain and Gini can be used for this
