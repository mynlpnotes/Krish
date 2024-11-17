# Create RGB image with PIL

```python
from PIL import Image

# This will create image of 100X100 of colour orange
image = Image.new("RGB", (100, 100), (255, 100, 0))

print(image.mode) # RGB
print(len(image.getbands())) # 3
```
