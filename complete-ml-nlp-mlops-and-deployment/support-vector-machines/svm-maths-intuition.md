# SVM Maths Intuition

* &#x20;Lets consider we have 2 coordinates x and y
* We have a best fit line - wTx + b = 0
* W is a vector perpendicular to the best fit line
* We have a coordinate -4, 0 and if we want to distance d
* Also we have one more coordinate 4,3 and we also want to find its distance
* &#x20;So for this we calculate the distance s and w, which is greater than 90
* So whenever the angle is greater than 0, then the distance between w and the point will be -ve
* So all the points below the best fit line will be -ve
* Similarly points above the plane, the angle will be between 0 and 90, so the distance will be +ve
* So we can say distance will be -ve for all the points below the line and it will be +ve for all the points above the plane
* Here we will create one more plane, which will be called as marginal plane, which passes through one of the coordinates
* We draw one more marginal plane on the other side
* So the equation for this line we take as wTx + b = +1 , we taking +1 as all the points above the plane are +ve
* Similarly for the other line we take it as wTx + b = -1
* In some research papers it is take as +k or -k also
* For computing the distance between the 2 lines, we add subtract this 2 values
* Unit vector means magnitude of vector is 1
* So to get the unit vector we divide it by ||w|| on both the sides
* This +2/ ||W|| is the cost function
*

    <figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>
* We need to maximize this cost function by changing the values of w,b
* We will be adding one more constraint
* y will be +1 if wTx + b >= 1&#x20;
* y will be -1 if wTx + b <= -1&#x20;
* This will be for all the correctly classified points
* 2nd constraint, For all correct points y \* (wTx + b) >= 1
*

    <figure><img src="../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>
