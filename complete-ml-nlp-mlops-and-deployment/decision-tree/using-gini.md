# Using Gini

*   <mark style="color:purple;background-color:purple;">**We need to select column which is giving us low impurity**</mark>

    <figure><img src="../../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>



| Class | Gender | Stay in Hostel |
| ----- | ------ | -------------- |
| 9     | M      | Y              |
| 10    | F      | N              |
| 8     | F      | Y              |
| 8     | F      | N              |
| 9     | M      | Y              |
| 10    | M      | N              |
| 11    | F      | Y              |
| 11    | M      | Y              |
| 8     | F      | Y              |
| 9     | M      | N              |
| 11    | M      | N              |
| 11    | M      | Y              |
| 10    | F      | N              |
| 10    | M      | Y              |
| 8     | F      | ?              |



| Class | Stay in Hostel | Total | P(Y) | P(N) |
| ----- | -------------- | ----- | ---- | ---- |
| 8     | 2Y, 1 N        | 3     | 0.66 | 0.33 |
| 9     | 2Y, 1 N        | 3     | 0.66 | 0.33 |
| 10    | 1Y, 3 N        | 4     | 0.25 | 0.75 |
| 11    | 3Y, 1 N        | 4     | 0.75 | 0.25 |



* G(8) =  1 – P(Y)2 – P(N)2 = 4/9
* G(9) = 4/9
* G(10) = 6/16
* G(11) = 6/16
* G(Class) =  (No.of instance of class N / Total No. of instance ) \* Gini of class N
* G(Class) = No. of instance of 8 / Total instance \* Gini of 8 + 9,10,11
* \= 3/14 \* 4/9 + 3/14 \* 4/9 + 4/14 \* 6/16 + 4/14 \* 6/16 = 0.404
* G(Gender) = 0.482
*

    <figure><img src="../../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>
* Gender is having higher Gini value
* Gini is called as gini impurity
* What is the probability that if this column is taken, that it will give more impurity
* Purity means that the output will be of 1 class
* So here we are supposed class column
* So we 1st start with Class node
* Then under each category of class, we find the instances and the outcomes
* Now we will take the instances under 8 and then again find the gini for class and gender
* G(Class—8) = 4/9
* G(Gender – 8) = 4/9
* For both the class and gender we are getting the same gini, in the previous step we have done on the basis of class , so here we will do on the basis of gender
*

    <figure><img src="../../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure>
* If input – 11, F 🡪 Y
* If input – 11, M 🡪 Y
