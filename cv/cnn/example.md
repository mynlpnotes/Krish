# ✈️ Example

* Input image is 100X100 RGB image
* Convolution (6 3X3 , Padding 0, Stride 1)
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Single convolution operation using 1st kernel
* We are doing 2D operation on each channel and dimension of the kernel
* We get 97X97 from each channel -> We will be adding output of all the channels pixel wise
* We apply 3D kernel in a 2D manner
*   Final output will be 97X97X6

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
