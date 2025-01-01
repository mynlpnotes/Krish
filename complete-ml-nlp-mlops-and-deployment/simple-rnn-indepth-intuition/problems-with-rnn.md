# Problems with RNN

Vanishing Gradient Problem:

* In ANN, we faced vanishing gradient problem, same problem we can face in RNN as well
* If we are working on a text generation problem, so the word will be predicted based on the previous words
* We can say it has short term dependencies on previous words
* if we have a long sentence, then the dependency can be on any word
* If a sentence has 100 words, then at t = 100 we will calculate back propagation
*

    <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

The long term dependency cannot be captured by RNN&#x20;

* If the length is 3
*   For updating weight Wh, we need add for 3 time stamps

    <figure><img src="../../.gitbook/assets/{677E83B6-C01C-445E-B633-83BE5911C588}.png" alt=""><figcaption></figcaption></figure>
* If the length is 50
* The derivative of sigmoid is between 0 and 0.25
*   So when we multiply this small terms the gradient will almost be 0, so there wont be weight updation

    <figure><img src="../../.gitbook/assets/{3EA0943B-24E6-4A61-8188-AFDB92B3064B}.png" alt=""><figcaption></figcaption></figure>
