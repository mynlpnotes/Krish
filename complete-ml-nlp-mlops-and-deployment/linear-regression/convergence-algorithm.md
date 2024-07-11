# Convergence Algorithm

*   To optimize the changes of Θ1 values

    <figure><img src="../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;We need to repeat the steps till convergence
* Suppose we start with point at the left and we have to reach global minima
* Whenever we say we derivative, it means we will be calculating the slope
* For calculating the derivative, we need to draw a tangent line
* We need to find whether its a +ve slope or -ve slope
* If the right side of the line is facing downwards, we says its a -ve slope
* if we get a -ve slope -> this means we need to add some positive value of Θ
* Then again we will repeat the step
* If we had started at the right, then we would have got +ve slope
* In this case we need to decrease the value of Θ
* The alpha used here is learning rate
* If this is a small value then it might take long time to converge
* If this is a big value, then it might keep jumping and not converge
* It controls the convergence
*

    <figure><img src="../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Here we have said Θ0 = 0 and Θ1 is changeable
* If both would have been non zero then it would have been as in figure right
*

    <figure><img src="../../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* := means continuous iterative process
* We will be calculating derivate wrt to Θ0 and then wrt Θ1 as well&#x20;
*

    <figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>
