# Instance based learning vs Model based learning

*   &#x20;

    <figure><img src="../../.gitbook/assets/image (15) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* **Instance:** If model is completely dependent on data, and for every prediction it is dependent on training data
* **Model based:** It tries to understand the pattern within the data and make a generalized model for prediction
* Model based is far better than instance based
* Dataset:

| No. of hours of Play | No. of hours of study | Pass/Fail |
| -------------------- | --------------------- | --------- |
|                      |                       |           |
|                      |                       |           |
|                      |                       |           |

*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* There can be some outliers also -> Someone study less still pass, some study more but still fail
* In instance based learning -> This will be like a domain expert
* When a new query comes, then the model knows training data, this model wont understand the pattern, it will just check the surrounding data
* If most of the points are pass then it will say that its Pass and vice versa
* Instance models: KNN
* Same problem if we consider in model based learning, then the model will understand the pattern in the data
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>
* Model will try to create a decision boundary
* Here we create a generalized format to learn the data
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
