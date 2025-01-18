# 🟢 Enhancing Images: Contrast Adjustment, Sharpening

* <mark style="color:purple;background-color:purple;">**We can apply CLAHE on grayscale**</mark>
* <mark style="color:purple;background-color:purple;">**To apply CLAHE on RGB we will have to apply on individual channels and then merge them, or instead we can also use LAB**</mark>
* <mark style="color:purple;background-color:purple;">**clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8, 8))**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**cl1 = clahe.apply(gray)**</mark>

```python
# CLAHE for greyscale

image = cv2.imread('./data/xray.jpg')

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8, 8))
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
cl1 = clahe.apply(gray)

# Save the CLAHE-enhanced grayscale image
cv2.imwrite('./temp/clahe_contrast_enhanced.jpg', cl1)  # Save as a JPG file

plt.figure(figsize=(8, 6))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title('Image RGB')

plt.subplot(1, 2, 2)
plt.imshow(cl1, cmap='gray')
plt.title('Enhanced Contrast')
```

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
