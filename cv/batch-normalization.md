# ✈️ Batch Normalization

* When we optimize with only 1 image at a time it is called SGD
  * We will take 1 image -> Train -> Calculate Loss -> Optimize -> Image 2
* If we have 100 images, then instead of 1 image, we can pass it in batches
* The more the images, more RAM will be required
* Based on research batches of 8, 16, 32 etc. are taken
* If we taking 1st batch for training (10 images of 100X100X3)
* If we apply 32 kernel of 3X3, padding 0, stride 1
* Then we will get 97X97X32 for each image
* We will take 1 channel of each image, for this we will calculate mean and std dev
* We have to normalize each pixel using (x - mean)/std. dev
* Each pixel will be normalized based on channel
* Similarly we will do for each channel
* Finally we will do scale and shift
* When we do normalization, values will be very small 0.1, 0.112, 0.123
* We can pick a value for scaling and then multiply to each value
* In shifting we can add some value to it
* <mark style="color:purple;background-color:purple;">**Scale and shift are learnable parameters**</mark>
