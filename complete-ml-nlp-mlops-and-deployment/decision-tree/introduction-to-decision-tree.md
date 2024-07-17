# Introduction to Decision Tree

* &#x20;Can be used for classification as well as regression
* Types: ID3(More than 2 splits) and CART(Only binary splits)
* sklearn uses CART
* DT also works like if elseif&#x20;
*

    <figure><img src="../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;Outlook as 3 different categories
* w.r.t outlook how many Y/N are there
* w.r.t sunny how many Y/N are there
* Do this for all categories
* Sunny is impure split as it having Y as well as N, we will split this further
* Overcast is pure split
* We will continue this split, till we get leaf node
*

    <figure><img src="../../.gitbook/assets/image (19) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;Purity is checked using entropy and gini impurity
*   What information to use for splitting is decided using information gain

    <figure><img src="../../.gitbook/assets/image (20) (1).png" alt=""><figcaption></figcaption></figure>
*
