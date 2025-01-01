# ✈️ Find Shapes and Bounding Boxes

* You can use contour approximation to detect specific shapes like triangles or rectangles. Contour approximation in OpenCV simplifies the shape of a contour by reducing the number of vertices while retaining the overall shape of the contour
*

```python
def get_shape(contour):
    # Approximate the contour
    # approx = cv2.approxPolyDP(curve, epsilon, closed)
    approx = cv2.approxPolyDP(contour, 0.01 * cv2.arcLength(contour, True), True)
    
    # Determine the shape based on the number of vertices
    if len(approx) == 3:
        shape = "Triangle"
    elif len(approx) == 4:
        # Check for rectangle or square
        x, y, w, h = cv2.boundingRect(approx)
        aspect_ratio = float(w) / h
        shape = "Square" if aspect_ratio == 1 else "Rectangle"
    elif len(approx) == 5:
        shape = "Pentagon"
    elif len(approx) == 6:
        shape = "Hexagon"
    elif len(approx) > 6:
        shape = "Polygon"
    else:
        shape = "Unknown"

    return (approx, shape)

image = cv2.imread('./data/beach-blue.jpg')

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
_, thresh = cv2.threshold(gray, 120, 180, cv2.THRESH_BINARY)
contours, _ = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)


# Create a mask for the filled contours
image_filled_contours = np.zeros_like(image)

# Sort contours by area and keep the largest ones
contours = sorted(contours, key=cv2.contourArea, reverse=True)[:1]  # Only take the top 5 largest contours

# Draw contours
for contour in contours:
    approx, shape = get_shape(contour)
    
    # color = (np.random.randint(100, 255), np.random.randint(100, 255), np.random.randint(100, 255))  # Random RGB color
    color = (255, 0 , 0)
    
    cv2.drawContours(image_filled_contours, [contour], -1, color, thickness=cv2.FILLED)
    
    # Calculate position for the text below the shape
    cx, cy = int(np.mean(approx[:, 0, 0])), int(np.mean(approx[:, 0, 1]))  # Calculate centroid
    text_position = (cx - 150, cy - 150)  # Move text down by 20 pixels
    
    cv2.putText(image_filled_contours, shape, (300,300), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 5)

# Combine filled contours with the original image
# You can choose to overlay the filled contours on the original image or keep them separate
# cv2.addWeighted(src1, alpha, src2, beta, gamma)
# alpha is weightage of first image and beta is weightage of second image
# gamma is brightness added to final result.
image_with_filled_contours = cv2.addWeighted(image, 0.5, image_filled_contours, 0.8, 1)

plt.imshow(image_with_filled_contours)
plt.title("Largest 5 Contours")
plt.grid(False)
plt.show()
```

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
