# Image Loading

```python
import cv2
from PIL import Image

# Load using OpenCV
# OpenCV loads images in BGR
image_cv = cv2.imread('./data/beach-blue.jpg')
image_swapped = image_cv[:, :, ::-1] # BGR to RGB

# Load using Pillow
# pillow loads images in RGB
image_pil = Image.open('./data/beach-blue.jpg')
```
