# Working of Convolution

* Convolve Function
* Stride
*   Kernel - Matrix of weights

    * Sobel filter
      *   For detecting horizontal edges

          <figure><img src="../../.gitbook/assets/image (6) (1).png" alt="" width="147"><figcaption></figcaption></figure>
    * Horizontal edges


* Convolution starts from left, filter is placed on the image and matrix multiplication is done
* We get value as 510 so we cap it at 255
* Kernel means by how many cells do we want to move the filter
* After applying the kernel we get 3X4
* The operation of moving kernel on the image is known an convolve function
*   It extracts only the relevant information based on the kernel

    <figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>
* We are able to reduce the size of the image
* If we increase stride then there will be more information loss
* if we reduce stride then image size will be more
