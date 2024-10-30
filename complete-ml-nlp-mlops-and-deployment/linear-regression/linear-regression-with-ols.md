# Linear Regression with OLS

* Ordinary Least Square
* <mark style="color:purple;background-color:purple;">**Using gradient descent our aim was to get the best fit line using optimization and using loss function**</mark>
* <mark style="color:purple;background-color:purple;">**OLS says that we can find the coefficients using formula**</mark>
* <mark style="color:purple;background-color:purple;">**OLS can be computationally expensive when working with very large datasets, especially if there are many features.**</mark>
* <mark style="color:purple;background-color:purple;">**Methods like gradient descent are often used as they’re computationally efficient and can handle large datasets and complex data structures more effectively than directly solving the OLS equation**</mark>
* <mark style="color:purple;background-color:purple;">**To minimize the SSE, we take the derivative of the SSE with respect to β\betaβ and set it to zero. This gives us the normal equation**</mark>
* $$β=(X  T  X)  −1  X  T  Y$$
*   We want to reduce the error as much as possible

    <figure><img src="../../.gitbook/assets/image (20) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>


*   &#x20;

    <figure><img src="../../.gitbook/assets/image (21) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (23) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (24) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (25) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* OLS will give similar results as linear regression
