# RGB vs HSV

**RGB:**

* Centre is 255, and as we move along the axes, it will decrease to 0
* So on the left plane, there will be some value of R and G but there wont be any value of B
* In the 2nd plane, there will be some value of R, G and some value of B as well
* <mark style="color:purple;background-color:purple;">**In RGB, we cannot just target any particular color, if we want to change B, then R and B will also change as well**</mark>
* <mark style="color:purple;background-color:purple;">**To create any color, R G and B will have to be added, so its a additive model**</mark>
*   There can be 16.7 million possible colors in RGB

    <figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

**HSV:**

* Hue of color (Degree)
* Saturation of color (Percent)
* Value of color (brightness) (Percent)
* <mark style="color:purple;background-color:purple;">**Cone kind of a structure, whereas RGB was cube**</mark>
* Hue correspond to the color component, there is a 360 wheel
* Red is from 330 to 30
* <mark style="color:purple;background-color:purple;">**0 means no saturation, so it means its white, as we increase the darker the color becomes**</mark>
* <mark style="color:purple;background-color:purple;">**High saturation means the color is vivid, rich, and pure.**</mark>
* <mark style="color:purple;background-color:purple;">**Low saturation means the color is dull, faded, or closer to gray**</mark>
* <mark style="color:purple;background-color:purple;">**V is brightness**</mark>&#x20;
*   In OpenCV Hue is 180 instead of 360, so the precision is of 0.5, S and V are 0 to 255

    <figure><img src="../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

So to separate any color it will be easier in HSV
