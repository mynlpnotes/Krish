# 🟢 Create RGBA image with PIL

* <mark style="color:purple;background-color:purple;">**RGBA: Adds an Alpha channel to RGB, representing transparency.**</mark>
* <mark style="color:purple;background-color:purple;">**PNG supports RGBA**</mark>
* <mark style="color:purple;background-color:purple;">**Create RGB image and then convert it to RGBA**</mark>
* <mark style="color:purple;background-color:purple;">**Use getbands() to get the number of channels**</mark>

```python
# Create image with orange color
image = Image.new("RGB", (100, 100), (255, 100, 0))
image_rgba = image.convert("RGBA")

print(image_rgba.size)
print(image_rgba.mode)
print(image_rgba.getbands())
image_rgba.show()
```
