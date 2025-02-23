# VggNet

* In Alexnet we started using Relu ⇒ To solve vanishing gradient problem
* Also we used Relu as it takes less computation, and derivative is easier to compute
* Proposed by oxford university in 2015
* If we use 3X3 and 5X5 then we will get more information in 3X3
* 5X5 ⇒ More information loss
* 3X3 ⇒ More computation
*

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In VGG idea of small filter ⇒ 3X3 and they stacked deep network
* Simple architecture
* They keep increasing filters in patterns and always use 3X3 filters
* Outperforms lenet and alexnet
* Input: 224X224
* Different configuration:
  * 19 layers (16 conv + 3 FC)
  * 16 layers (13 + 3)
  * 11 layers (8 + 3)
* Predicts total 1000 classes
*
