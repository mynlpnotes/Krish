# Create RGBA image with PIL

* RGBA: Adds an Alpha channel to RGB, representing transparency.
* PNG supports RGBA

```python
# Create image with orange color
image = Image.new("RGB", (100, 100), (255, 100, 0))
image_rgba = image.convert("RGBA")

print(image_rgba.size)
print(image_rgba.mode)
print(image_rgba.getbands())
image_rgba.show()
```
