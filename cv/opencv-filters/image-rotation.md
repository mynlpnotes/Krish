# Image Rotation

We can rotate images by specific angles. Below are the example:

* cv2.ROTATE\_90\_CLOCKWISE
* cv2.ROTATE\_90\_COUNTERCLOCKWISE
* cv2.ROTATE\_180

```python
# Rotate

image_r = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
rotated_90c = cv2.rotate(image_r, cv2.ROTATE_90_CLOCKWISE)
rotated_90ac = cv2.rotate(image_r, cv2.ROTATE_90_COUNTERCLOCKWISE)
rotated_180 = cv2.rotate(image_r, cv2.ROTATE_180)

# Display the result
plt.figure(figsize=(20, 16))

plt.subplot(4, 1, 1)
plt.imshow(image_r)
plt.title('Original')

plt.subplot(4, 1, 2)
plt.imshow(rotated_90c)
plt.title('ROTATE_90_CLOCKWISE')

plt.subplot(4, 1, 3)
plt.imshow(rotated_90ac)
plt.title("ROTATE_90_COUNTERCLOCKWISE")

plt.subplot(4, 1, 4)
plt.imshow(rotated_180)
plt.title("ROTATE_180")

# Adjust the space between subplots
plt.subplots_adjust(hspace=0.5)  # Increase hspace for more vertical spacing
```
