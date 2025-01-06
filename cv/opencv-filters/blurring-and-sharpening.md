# 🟠 Blurring and Sharpening

* <mark style="color:purple;background-color:purple;">**Blurring is useful for reducing noise.**</mark>
  * <mark style="color:purple;background-color:purple;">**Gaussian blur is a technique to reduce noise and detail by averaging pixel values in a neighborhood, weighted by a Gaussian kernel (a bell-shaped curve). A larger kernel size will result in more blurring, while a smaller kernel size will cause less blurring.**</mark> Decreasing it (e.g., (3, 3)) will reduce the blurring effect.
  * (5, 5) is the size of the kernel, which determines how much the image will be blurred. Larger values result in a blurrier image.
  * 0 specifies the standard deviation for the Gaussian function. Here, it is automatically calculated based on the kernel size.
* <mark style="color:purple;background-color:purple;">**Sharpening enhances edges.**</mark>
  * <mark style="color:purple;background-color:purple;">**The sharpening effect is controlled by the values in the convolution kernel applied with cv2.filter2D(). The larger the center value (the 5 in your kernel), the sharper the result. The surrounding values (-1 in your case) determine how much contrast is applied between the current pixel and its neighbors.**</mark>
  * Increase sharpening by increasing the center value (e.g., changing 5 to 7 or 9).
  * Decrease sharpening by reducing the center value (e.g., changing 5 to 3 or 1).

```python
# Load the image
image = cv2.imread('./data/beach-blue.jpg')

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

kernelSizes = [(3, 3), (9, 9), (15, 15)]


# Blurring the Image
blurred_3 = cv2.GaussianBlur(image_rgb, kernelSizes[0], 0)
blurred_9 = cv2.GaussianBlur(image_rgb, kernelSizes[1], 0)
blurred_15 = cv2.GaussianBlur(image_rgb, kernelSizes[2], 0)


# Sharpening the Image
# kernel_1 = np.array([[0, -1, 0], [-1, 5, -1], [0, -1, 0]])
kernel_2 = np.array([[-1,-1,-1], [-1,9,-1], [-1,-1,-1]])
sharpened = cv2.filter2D(image_rgb, -1, kernel_2)
# sharpened = cv2.filter2D(sharpened, -1, kernel_2)
# Display the results
plt.figure(figsize=(30, 15))


plt.subplot(1, 5, 1)
plt.imshow(image_rgb)
plt.title('Original')

plt.subplot(1, 5, 2)
plt.imshow(blurred_3)
plt.title('Blurred_3')

plt.subplot(1, 5, 3)
plt.imshow(blurred_9)
plt.title('Blurred_9')

plt.subplot(1, 5, 4)
plt.imshow(blurred_15)
plt.title('Blurred_15')

plt.subplot(1, 5, 5)
plt.imshow(sharpened)
plt.title('Sharpened')

plt.show()
```

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
