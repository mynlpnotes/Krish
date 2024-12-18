# 🟠 Contour

*   <mark style="color:purple;background-color:purple;">**Contour is a curve that connects all the continuous points along the boundary of an object that have the same coloir or intensity.**</mark>

    <mark style="color:purple;background-color:purple;">**or in-short :**</mark>

    <mark style="color:purple;background-color:purple;">**Contours are the boundaries of objects detected in an image**</mark>
* <mark style="color:purple;background-color:purple;">**Using cv2.threshold we will create the threshold**</mark>
* <mark style="color:purple;background-color:purple;">**Usinv cv2.findContours we can find the contours**</mark>

```python
image = cv2.imread('./data/beach-blue.jpg')

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
_, thresh = cv2.threshold(gray, 120, 180, cv2.THRESH_BINARY)
contours, _ = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)


# Create a mask for the filled contours
image_filled_contours = np.zeros_like(image)

# Sort contours by area and keep the largest ones
contours = sorted(contours, key=cv2.contourArea, reverse=True)[:5]  # Only take the top 5 largest contours

# Draw contours
for contour in contours:
    color = (np.random.randint(100, 255), np.random.randint(100, 255), np.random.randint(100, 255))
    # color = (255, 0, 0)  # Static RGB color
    cv2.drawContours(image_filled_contours, [contour], -1, color, thickness=cv2.FILLED)

# Combine filled contours with the original image
# You can choose to overlay the filled contours on the original image or keep them separate
# cv2.addWeighted(src1, alpha, src2, beta, gamma)
# alpha is weightage of first image and beta is weightage of second image
# gamma is brightness added to final result.
image_with_filled_contours = cv2.addWeighted(image, 0.5, image_filled_contours, 0.8, 0.2)

plt.imshow(image_with_filled_contours)
plt.title("Largest 5 Contours")
plt.grid(False)
plt.show()
```

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
