# 🟢 EXIF Details

* <mark style="color:purple;background-color:purple;">**Metadata in images, like camera settings, date, etc**</mark>
* <mark style="color:purple;background-color:purple;">**Pillow doesn't provide a built-in way to directly modify EXIF data.**</mark>

```python
from PIL import Image, ExifTags

image = Image.open('./data/GP_PXL_20240926_003004774.jpg')
exif_data = image._getexif()

for tag, value in exif_data.items():
    tag_name = ExifTags.TAGS.get(tag, tag)
    print(f"{tag_name}: {value}")
    
# Output:
# ImageWidth: 2268
# ImageLength: 4032
# GPSInfo: {16: 'M', 17: 268.0}
# ResolutionUnit: 2
# ExifOffset: 244
# Make: Google
# Model: Pixel 4a
# Software: HDR+ 1.0.540104767zdr
# Orientation: 1
# DateTime: 2024:09:26 06:00:04
# YCbCrPositioning: 1
# XResolution: 72.0
```
