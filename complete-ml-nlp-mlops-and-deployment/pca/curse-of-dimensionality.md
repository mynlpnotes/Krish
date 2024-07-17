# Curse of Dimensionality

* Principal component analysis
* Also called dimensionality reduction
* Dataset is having 500 features
* For M1 we provided 3 features, M2 we provided 6 features and so on
* Acc2 will be more compared to Acc1
* Acc3 may be more compared to Acc2
* In M4 there might be scenario that some of the features might be not important, here our accuacy might decrease compared to Acc3
* In M6 our accuracy might be even more decreased
* At M4 we can say model is overfeeded
* Models should be given no. of features so that accuracy is increasing and not more than that
* Since model is getting trained on features which are not important then it might led to confusion so performance will decrease
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>


* Model performance will degrade as calculations will happen for that many dimensions
*   Person keeps on adding requirement while buying house, so price will increase, some parameters might not be much important, so for that price wont increase much, so as keep adding parameters then price wont be able to predict correctly

    <figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

Ways to remove curse of dimensionality:

1. Feature selection: Take only important features
2. Dimensionality reduction: Feature extraction - PCA

* Feature extraction means extracting a feature from a set of features, where we will be capturing much essence of the features
*
