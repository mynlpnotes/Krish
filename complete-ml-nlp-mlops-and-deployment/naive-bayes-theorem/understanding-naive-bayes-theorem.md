# Understanding Naive Bayes Theorem

* Used to solve binary and multi class classification
* Basic idea about probability is required
* <mark style="color:red;background-color:purple;">**Never use dimension reduction with Naïve Bayes as data will lose its independence**</mark>
* <mark style="color:purple;background-color:purple;">**If there are some instance which was not available, then the entire equation becomes 0**</mark>
* <mark style="color:purple;background-color:purple;">**Independent event means one outcome is not hampering or not changing the probability of other outcome**</mark>
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In dependent event, one outcome is changing the probability of other outcome
* P(B/A) -> Probability of B given A has occurred
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>
* &#x20;P( A and B) is same as P(B and A)
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;The algorithm that uses this bayes theorem is called naive bayes algorithm
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
