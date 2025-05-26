# Using entropy and information gain

* Entropy means randomness or degree of freedom
*

    <figure><img src="../../../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>
* 2 is having higher entropy
*

    <figure><img src="../../../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>
* Based on entropy we can find information gain
* <mark style="color:purple;background-color:purple;">**Information gain = Ebefore - Eafter**</mark>
* We have 14 records
* n(Y) – 8 – number of Y records
* n(N) – 6
*   E(Stay in hostel) = -P(Y)log P(Y) - P(N)log P(N)

    \= 8/14 \* log (8/14) – 6/14 \* log(6/14)

    \= 0.98522
* E (class = 8) = -2/3 \* log(2/3) – 1/3 \*log(1/3) =  0.918
* E (class = 9) = -2/3 \* log(2/3) – 1/3 \*log(1/3) =  0.918
* E (class = 10) = -1/4 \* log(1/4) – ¾ \* log(3/4) =  0.811
* E(class = 11) = – ¾ \* log(3/4) -1/4 \* log(1/4)  =  0.811
* I(Class) = 3/14 \* 0.918 + 3/14 \* 0.918 + 4/14 \* 0.811 + 4/14 \* 0.811 = 0.8574 🡪 information from class
* IG(Class) = 0.98522 – 0.8574 = 0.1278
* IG(Gender)
* E(M) = - 5/8 \* log(5/8) – 3/8 \* log(3/8) = 0.954
* E(F) = -3/6 \* log(3/6) – 3/6 \* log(3/6) = 1
* I(Gender) = 8/14 \* 0.954 + 6/14 \* 1 = 0.974
* IG(Gender) = 0.98522 – 0.974 = 0.01
* Class is having more information gain as compared to gende
* Entropy means randomness, so if we use this column then how much randomness can we reduce
