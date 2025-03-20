# Object Detection

* Given an image, we want to know where the object is in the image
* This is called object/image localization ⇒ image contains only single class and only a single instance
* We predict the bounding box of single object
* If there are multiple classes / instances then it is object detection
* The goal is to detect all the objects, classify them and also draw bounding box
* In object detection there will be 2 outputs ⇒ classes and bbox regressor
* For each object instance there will be class and bbox
*

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



* In contours using openCV we drew boundary on the image
* We are trying to detect object here
*
