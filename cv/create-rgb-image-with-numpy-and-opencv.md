# Create RGB Image with Numpy and OpenCV

* <mark style="color:purple;background-color:purple;">**Here we 1st need to create an array and then we need to give pixel values**</mark>

```python
import numpy as np
import cv2

# Create a blank image with black pixels
image_opencv = np.zeros((500, 500, 3), np.uint8) 
# Fill the image with orange color (BGR values)
image_opencv[:] = (0, 100, 255)

print(image_opencv.shape) #(500, 500, 3)
print(len(image_opencv))  # 500

# Display the image
cv2.imshow('Orange Image', image_opencv)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
