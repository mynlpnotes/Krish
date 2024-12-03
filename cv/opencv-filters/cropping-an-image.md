# Cropping an image

Cropping is done by slicing the image array

The top leftmost point of image is 0,0

* image\[y1:y2, x1:x2]
* y1:y2: Defines the height
* x1:x2: Defines the width

```python
# Cropping an image
cropped_image = image[200:600, 200:600]

print(cropped_image.shape)

plt.imshow(cropped_image)
plt.title("Cropped Image")
plt.show()
```

*

    <figure><img src="../../.gitbook/assets/{BB15D753-E741-4754-AB4D-A2FC710D7724}.png" alt=""><figcaption></figcaption></figure>
