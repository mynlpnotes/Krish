# Hue, Saturation, Contrast, Shadows

* Hue: The attribute of a color (red, blue, yellow).
* Saturation: The intensity or purity of a color.
* Contrast: The difference between light and dark areas of an image.
* Shadows: The darker areas of an image where details are less visible.

```python
import numpy as np
import seaborn as sns

# Load the image and convert to HSV
image = cv2.imread('./data/beach-blue.jpg')
image_hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)

# Plot histograms for Hue, Saturation, and Value
hue_hist = cv2.calcHist([image_hsv], [0], None, [180], [0, 180])
saturation_hist = cv2.calcHist([image_hsv], [1], None, [256], [0, 256])
value_hist = cv2.calcHist([image_hsv], [2], None, [256], [0, 256])

warm_val = (hue_hist > 160 & hue_hist < 180) or ()
# Set Seaborn styling
sns.set(style="whitegrid", palette="muted", font_scale=1.2)

# Plotting
plt.figure(figsize=(16, 6))

# Plot the Hue histogram
plt.subplot(1, 3, 1)
sns.lineplot(x=np.arange(180), y=hue_hist[:, 0], color='orange')
plt.title('Hue Histogram', fontsize=14, fontweight='bold')
plt.xlabel('Hue Value', fontsize=12)
plt.ylabel('Frequency', fontsize=12)
plt.grid(True)

# Plot the Saturation histogram
plt.subplot(1, 3, 2)
sns.lineplot(x=np.arange(256), y=saturation_hist[:, 0], color='green')
plt.title('Saturation Histogram', fontsize=14, fontweight='bold')
plt.xlabel('Saturation Value', fontsize=12)
plt.ylabel('Frequency', fontsize=12)
plt.grid(True)

# Plot the Value histogram
plt.subplot(1, 3, 3)
sns.lineplot(x=np.arange(256), y=value_hist[:, 0], color='blue')
plt.title('Value (Brightness) Histogram', fontsize=14, fontweight='bold')
plt.xlabel('Value (Brightness)', fontsize=12)
plt.ylabel('Frequency', fontsize=12)
plt.grid(True)

# Adjust the layout for better spacing
plt.tight_layout()

# Display the plots
plt.show()
```

*

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
