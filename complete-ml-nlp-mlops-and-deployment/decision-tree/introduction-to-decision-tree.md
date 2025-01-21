# Introduction to Decision Tree

* &#x20;Can be used for <mark style="color:purple;background-color:purple;">**classification as well as regression**</mark>
* <mark style="color:purple;background-color:purple;">**Types: ID3(More than 2 splits) and CART(Only binary splits)**</mark>
* <mark style="color:purple;background-color:purple;">**sklearn uses CART**</mark>
* <mark style="color:purple;background-color:purple;">**If a node is having one output then it is called as pure node**</mark>
* <mark style="color:purple;background-color:purple;">**If the data is separable then we can use logistic regression, but if the data is very irregular then in such scenario we can go for decision tree**</mark>
* <mark style="color:purple;background-color:purple;">**Good at handling missing value**</mark>
* DT also works like if elseif&#x20;
*

    <figure><img src="../../.gitbook/assets/image (363).png" alt=""><figcaption></figcaption></figure>
* Outlook as 3 different categories
* w.r.t outlook how many Y/N are there
* w.r.t sunny how many Y/N are there
* Do this for all categories
* Sunny is impure split as it having Y as well as N, we will split this further
* Overcast is pure split
* We will continue this split, till we get leaf node
*

    <figure><img src="../../.gitbook/assets/image (364).png" alt=""><figcaption></figcaption></figure>
* Purity is checked using entropy and gini impurity
*   What information to use for splitting is decided using information gain

    <figure><img src="../../.gitbook/assets/image (365).png" alt=""><figcaption></figcaption></figure>
*
