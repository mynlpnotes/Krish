# Normalizing weights and assigning bins

* &#x20;The sum of updated weights is not 1
* So we need to normalize it (Divide each value by 0.697)
* We need to send wrong records to next DT stump
* To ensure mostly wrong records goes to next DT stump, we create bins
* Bins created based on the normalized weights
* Wrong records will have big bins
* So we will send records having big bins to next DT stump
*

    <figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>
