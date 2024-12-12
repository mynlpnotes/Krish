# LAB Color Space

To apply CLAHE on RGB images we will use LAB colour space. LAB color space is a color model designed to approximate human vision, often used for image processing tasks like color correction and contrast adjustment.

* L Channel (Lightness)
  * Values range from 0 (black) to 100 (white).
  * Modifying this channel affects the brightness and contrast of the image without altering its color.
* A Channel (Green-Red)
  * Represents the color information on the green to red axis.
  * Negative values indicate green, and positive values indicate red.
* B Channel (Blue-Yellow)
  * Represents the color information on the blue to yellow axis.
  * Negative values indicate blue, and positive values indicate yellow

```python
# Convert to LAB color space
lab = cv2.cvtColor(image, cv2.COLOR_BGR2LAB)

# Split the LAB image into its channels
l_channel, a_channel, b_channel = cv2.split(lab)

# Apply CLAHE to the L (lightness) channel
clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8, 8))
cl1 = clahe.apply(l_channel)

# Merge the CLAHE enhanced L-channel with the original a and b channels
lab_clahe = cv2.merge((cl1, a_channel, b_channel))

# Convert LAB back to RGB for display
image_clahe = cv2.cvtColor(lab_clahe, cv2.COLOR_LAB2RGB)

# Display the result
plt.figure(figsize=(8, 6))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title('Image RGB')

plt.subplot(1, 2, 2)
plt.imshow(image_clahe)
plt.title("CLAHE Applied to RGB Image")
```

<figure><img src="../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>
