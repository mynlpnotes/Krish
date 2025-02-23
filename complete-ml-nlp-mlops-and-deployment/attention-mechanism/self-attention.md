# Self Attention

* This process of doing re-weighing is knows as self-attention
*

    <figure><img src="../../.gitbook/assets/image (546).png" alt=""><figcaption></figcaption></figure>

1. DOT PRODUCT - Of V1, V2... with themselves
2. This gives some scores, which is passed to normalization - S31, S32, S33, S34
3. Then it goes to normalization, such that sum of S31, S32, S33, S34 = 1 (Same is done using softmax)
4. After having this weights, we multiply it with their respective vectors
5. Similarly we do for all vector – V1, V2, V3, V4

* <mark style="color:purple;background-color:green;">**This are called attention blocks**</mark>
* <mark style="color:purple;background-color:green;">**There are no trainable weights here**</mark>



* If we call V3 as QUERY
* V1, V2, V3, V4 as KEYS
* V1, V2, V3, V4 when multiplying is known as VALUES
* To introduce weights, there will be a vector MQ which can be multiplied with QUERY
* Similarly MK can be multiplied with KEYS
* MV can be multiplied with VALUES
* This are trainable weights
* They are randomly initialized
* The dimension after multiplication should not change
* So if Vi is 1XK then M will be KXK so output will be 1XK
* Representing the same in a different manner       &#x20;

<figure><img src="../../.gitbook/assets/image (547).png" alt=""><figcaption></figcaption></figure>

* We are doing linear transformation by multiplying vector with matrices
* DOT product of query and keys is done after that
* This will give some scores(which are vectors)
* After that we do normalization
* This will give some weights Wij
* After that we do matrix multiplication by multiplying weight with values
* <mark style="color:purple;background-color:green;">**This is known as self attention blocks**</mark>
* We can also stack attention blocks
* In operations like NER,

<figure><img src="../../.gitbook/assets/image (548).png" alt=""><figcaption></figcaption></figure>

* To extract information like this to get name, place, org we need attention mechanism
* In backpropagation, the context Y1… will not be correct, so it backpropagate and the randomly initialized matrices will be updated
* <mark style="color:purple;">**Here it is not sequential approach, we are not passing sequentially**</mark>
* <mark style="color:purple;">**Some times one matrix might not be enough, so we can have multi attention mechanism (AM1 for name, AM2 for place, AM3 for Org)**</mark>
*

    <figure><img src="../../.gitbook/assets/image (549).png" alt=""><figcaption></figcaption></figure>
* This are called heads
* If we have 3 different matrices
* Then we will get 3 different scores and 3 different weight matrixes
* After that we concatenate and dense
* This is known as muti head attention
* This multi head attention blocks can also be stacked
* ![](<../../.gitbook/assets/image (550).png>)
* In his way, we can get more context
