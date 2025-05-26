# KNN Classification and Regression Intuition

* Can be used for <mark style="color:purple;background-color:purple;">**classification as well as regression**</mark>
* Can be used for binary categories as well as multiclass categories
* <mark style="color:purple;background-color:purple;">**Lazy learning algorithm**</mark>
* <mark style="color:purple;background-color:purple;">**Model size will increase as the number of training instances increase**</mark>
* <mark style="color:purple;background-color:purple;">**It will do calculations at run time**</mark>
* <mark style="color:purple;background-color:purple;">**If datasize is huge, then it should not be used**</mark>
* <mark style="color:purple;background-color:purple;">**If the data is mix of categorical + numerical then convert all the categorical data into vector space**</mark>

**Classification Steps:**

1. <mark style="color:purple;background-color:purple;">**Initialize value of K - No. of neighbors -- This is a hyperparameter**</mark>
2. <mark style="color:purple;background-color:purple;">**Find K nearest neighbors for the test data**</mark>
3. <mark style="color:purple;background-color:purple;">**From those K values, how many neighbors belong to which category - The category to which maximum neighbours belong will be the output**</mark>

*   &#x20;

    <figure><img src="../../../.gitbook/assets/image (357).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**The nearest neighbors can be found using - Euclidean distance, Manhattan distance**</mark>
*   &#x20;

    <figure><img src="../../../.gitbook/assets/image (358).png" alt=""><figcaption></figcaption></figure>

**Regression:**

* &#x20;For new test data, we will find the 5 nearest neighbors
* <mark style="color:purple;background-color:purple;">**We will take the average of the outputs of the neighbors**</mark>
*   &#x20;

    <figure><img src="../../../.gitbook/assets/image (359).png" alt=""><figcaption></figcaption></figure>



* <mark style="color:purple;background-color:purple;">**This process of calculating nearest neighbors is time consuming**</mark>
* <mark style="color:purple;background-color:purple;">**So we use variants of KNN like KD Tree , Ball Tree, we basically optimize this entire distance calculation**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (360).png" alt=""><figcaption></figcaption></figure>
