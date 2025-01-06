# 🟢 Color Thresholding

* <mark style="color:purple;background-color:purple;">**Color thresholding allows you to filter specific colors from the image and create a mask out of it**</mark>
* <mark style="color:purple;background-color:purple;">**Use cv2.inRange to create by specifying the higher value and low value of the colour to be replaced**</mark>
* <mark style="color:purple;background-color:purple;">**Use cv2.bitwise\_and to apply the mask on the image**</mark>

```python
import matplotlib.pyplot as plt

lower_blue = np.array([80, 0, 50])
upper_blue = np.array([120, 255, 255]) 

image = cv2.imread('./data/beach-blue.jpg')
image_hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Create mask and apply it
mask = cv2.inRange(image_hsv, lower_blue, upper_blue)
# source image, second source image to perform the and operation with, mask that controls which pixels from the source images are used in the output.

res = cv2.bitwise_and(image_rgb, image_rgb, mask=mask)

mask_inv = cv2.bitwise_not(mask)
res2 = cv2.bitwise_and(image_rgb, image_rgb, mask=mask_inv)
# mask is an optional binary mask. If provided, the operation is applied only to the pixels where the mask value is non-zero.

# Plot the mask to see the region detected and the result
plt.figure(figsize=(12, 6))

# Plot original image
# plt.subplot(nrows, ncols, index)

plt.subplot(1, 4, 1)
plt.imshow(image_rgb)
plt.title('Original Image')
plt.grid(False)  # Turn off grid

# Plot the mask (binary image where white represents detected blue regions)
plt.subplot(1, 4, 2)
plt.imshow(mask, cmap='gray')
plt.title('Blue Mask (Binary)')
plt.grid(False)  # Turn off grid

# Plot the blue-filtered result
plt.subplot(1, 4, 3)
plt.imshow(res)
plt.title('Blue Region Filtered')
plt.grid(False)  # Turn off grid

# Plot the inv blue-filtered result
plt.subplot(1, 4, 4)
plt.imshow(res2)
plt.title('Blue Region Filtered')
plt.grid(False)  # Turn off grid

plt.show()
```

```python
orange_image = np.zeros_like(image_rgb)
orange_image[:, :] = [255, 180, 0]

mask_inv = cv2.bitwise_not(mask)

orange_part = cv2.bitwise_and(orange_image, orange_image, mask=mask_inv)
#  keeps only the red regions in the areas where mask_inv is white

final_result = cv2.add(res, orange_part)

# Plot the original image, blue-filtered result, and final result
plt.figure(figsize=(15, 5))

# Plot original image
plt.subplot(1, 3, 1)
plt.imshow(image_rgb)
plt.title('Original Image')
plt.grid(False)  # Turn off grid

# Plot the blue-filtered result
plt.subplot(1, 3, 2)
plt.imshow(res)
plt.title('Blue Region Filtered')
plt.grid(False)  # Turn off grid

# Plot the final result (blue regions + orange background)
plt.subplot(1, 3, 3)
plt.imshow(final_result)
plt.title('Blue Region with Orange Background')
plt.grid(False)  # Turn off grid

plt.show()
```

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
