# Sequential Memory

* A B C D ……….Z
* We know after A, B will come and so on
* But if we reverse it, then it will be little difficult to remember
* If we apply RNN here, we will pass this data and then try to predict the next letter
* That means sequential data is easier to remember
* <mark style="color:purple;background-color:green;">**RNNs are abstract concept of sequential memory**</mark>

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

* Depending on the speed of car, we need to decide whether we should decrease the speed or change the lane
* For this we need to understand where the car was at t-1 and where it is at t
* Based on this difference we can guess the speed of the car
* To remember the position at t-1 we need to have memory
* So we need to know what happen in the past
* This is known as sequential memory
* <mark style="color:purple;background-color:green;">**RNN remember what happen in the past and then makes prediction for future**</mark>
