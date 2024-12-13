---
hidden: true
---

# Kd-Tree

* K dimensional tree
* Approach to reduce computational complexity of knn
* Arrange the data based on decision tree
* If new dataset comes then we can avoid calculations on all the data points
* We can reduce the calculations to less than half
* Training data
* {(1,2),(2,3),(2,4),(3,6),(4,2),(5,7),(6,8),(7,1),(8,5),(9,1),(9,3)} 🡪 (x,y)
* X = 1,2,3,3,4,5,6,7,8,8,9
* First arrange in ascending and then take the middle value
* Middle value is 5
* So the root node will be (5,7)
* Then again do the same on both the sides repeatedly
*

    <figure><img src="../../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* If the input is 10 and if k = 3, then neighbour will be (9,3), (9,1) and (8,5)
* So output will be ( 5 + 1 + 3) / 3 = 3
