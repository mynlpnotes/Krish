# Create B/W or gray-scale image with PIL

```python
from PIL import Image
image_bw = Image.new("L", (100, 100), (100))

print(image_bw.mode) # L
print(image_bw.getbands())  # ('L',)
```
