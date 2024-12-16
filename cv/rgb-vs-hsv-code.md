# RGB vs HSV Code

* <mark style="color:purple;background-color:purple;">**We can use COLOR\_RGB2HSV**</mark>
* <mark style="color:purple;background-color:purple;">**HSV is not so much friendly for eyes, but is good for image processing**</mark>

```python
import matplotlib.pyplot as plt

# Load image in RGB
image = cv2.imread('./data/beach-blue.jpg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# Plot both RGB and HSV
# Nrow, Ncol, Index
plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title('RGB Image')

plt.subplot(1, 2, 2)
plt.imshow(image_hsv)
plt.title('HSV Image')

plt.show()
```

*

    <figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
