# Working of NN - Training Flow

* RGB is input
* After forward loss, we will calculate loss using loss function
* Based on the loss, we will optimize weights, based on optimizers(GD, ADAM and others)
* Optimizers use back propagation
* Weight will be update 1st in last layer and then so on
*   We will try to minimize loss

    <figure><img src="../../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>
