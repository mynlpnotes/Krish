# Create RGB image with PIL

* <mark style="color:purple;background-color:purple;">**Here to create image we just need to specify pixel value once**</mark>

```python
from PIL import Image

# This will create image of 100X100 of colour orange
image = Image.new("RGB", (100, 100), (255, 100, 0))

print(image.mode) # RGB
print(len(image.getbands())) # 3
```
