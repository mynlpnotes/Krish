---
hidden: true
---

# Working with PIL

```
from PIL import Image
```

| Code                                                | Usage                                                         |
| --------------------------------------------------- | ------------------------------------------------------------- |
| image = Image.new("RGB", (100, 100), (255, 100, 0)) | To create new image, we just need to specify pixel value once |
| print(image.mode)                                   | Output: RGB                                                   |
| print(len(image.getbands()))                        | Output: 3                                                     |
| image\_bw = Image.new("L", (100, 100), (100))       | To create grayscale image                                     |
