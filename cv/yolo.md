# Yolo

* Clone yolov5 repo
* Install yolov5
* Download data from roboflow - hardhat - raw version
* While downloading using yolov5 sample
* It has train test, test and val folders and each folder has images and labels
* data.yaml ⇒ has information about number of classes and lables
* We keep images and labels in different structure, coz so that if data annotation team makes any correction then they would have to store only labels.txt

**Project Structure:**

hardhatdata

* images
  * train
    * image1
    * image2
  * test
    * image3
    * image4
  * val
    * image5
    * image6
* labels
  * train
    * image1.txt ⇒ it will contain the index and its bounding box info, in 1 image there can be multiple object instances
    * image2.txt
  * test
    * image3.txt
    * image4.txt
  * val
    * image5.txt
    * image6.txt

yolo

* copy coco.yaml ⇒ hardhat.yaml ⇒ replace class names here and data path



* cd yolov5
* python train.py --weights "yolov5s.pt" --data "hardhatdata.yaml" --epochs 5 --device 0
* Better to train on GPU
*   In val we have 20 images, in which there are total 65 instances (18 of head, 45 of helmet....), we also have precision and recall here

    <figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

