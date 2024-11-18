# Alpha using OpenCV

* OpenCV doesn't directly support adding an alpha channel to an image, you can achieve this by creating a new image with 4 channels (BGRA) and copying the original image data into it

```python
# Create a new image with 4 channels (BGRA)
bgra_opencv = np.zeros((image_rgb.shape[0], image_rgb.shape[1], 4), dtype=np.uint8)

# Copy the original image data into the BGR channels
bgra_opencv[:, :, :3] = image_rgb

# Set the alpha channel to 255 (fully opaque)
bgra_opencv[:, :, 3] = 255
```
