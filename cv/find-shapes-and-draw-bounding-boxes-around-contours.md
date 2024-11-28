# Find shapes and draw Bounding Boxes Around Contours

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the image
image = cv2.imread('./data/beach-blue.jpg')

# Convert to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Apply thresholding to get a binary image
_, thresh = cv2.threshold(gray, 120, 180, cv2.THRESH_BINARY)

# Find contours in the binary image
contours, _ = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

# Sort contours by area and keep the largest ones
contours = sorted(contours, key=cv2.contourArea, reverse=True)[:1]  # Only take the top 5 largest contours

# Create a copy of the original image to draw on
image_with_bboxes = image.copy()

# Loop through each contour to draw bounding boxes
for contour in contours:
    print(f"length of contour : {len(contour)}")
    # Draw the bounding box around the contour
    x, y, w, h = cv2.boundingRect(contour)  # Get the bounding box coordinates
    cv2.rectangle(image_with_bboxes, (x, y), (x + w, y + h), (0, 0, 255), 10)  # Draw bounding box in yellow

# Display the result
plt.imshow(cv2.cvtColor(image_with_bboxes, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Bounding Boxes Around Contours")
plt.axis('off')  # Turn off axis
plt.show()

```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
