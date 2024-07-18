# Selecting New Datapoints for Next tree

* &#x20;Iterative process
* Select random values between 0 and 1
* If random number is 0.5 then we will check in which bin does this number come
* If next is 0.10 then 2nd record will get selected
* Next if 0.6 is selected then 6th record is selected again
* Next if 0.75 then again 6th record is selected
* Using this we will select 7 records
* So the 6th record is getting selected again and again
* This will be our new dataset which will be passed for training to next DT stump
*

    <figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
* &#x20;Again weights will get calculated, performance of stump will be calculated and so on
*

    <figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
