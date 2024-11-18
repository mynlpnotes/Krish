# EXIF Orientation

The 8 EXIF orientation values are numbered 1 to 8.

* 1 = 0 degrees: the correct orientation, no adjustment is required.
* 2 = 0 degrees, mirrored: image has been flipped back-to-front.
* 3 = 180 degrees: image is upside down.
* 4 = 180 degrees, mirrored: image has been flipped back-to-front and is upside down.
* 5 = 90 degrees: image has been flipped back-to-front and is on its side.
* 6 = 90 degrees, mirrored: image is on its side.
* 7 = 270 degrees: image has been flipped back-to-front and is on its far side.
* 8 = 270 degrees, mirrored: image is on its far side.

```python
# Print EXIF tags and values
import piexif

exif_dict = piexif.load(image.info.get('exif', b''))
print(exif_dict)

# Update orientation to 5 (Mirrored and rotated 90° counterclockwise)
# Tag 274 refers to the 'Orientation' tag in EXIF
exif_dict["0th"][piexif.ImageIFD.Orientation] = 5

# Insert the modified EXIF data back into the image
exif_bytes = piexif.dump(exif_dict)
image.save('./temp/GP_PXL_20240926_003004774_with_updated_exif.jpg', exif=exif_bytes)
```
