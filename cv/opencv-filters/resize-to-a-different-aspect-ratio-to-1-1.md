# 🟢 Resize to a different aspect ratio to 1:1

* <mark style="color:purple;background-color:purple;">**Yolo uses square resolution, that means 1:1 ⇒  length = height**</mark>

```python
height, width, _ = image.shape

image_ = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
new_width = int(width/8)
new_height = int(height/8)

print(image.shape)
print(new_width, new_height)


# new_points = (new_width, new_height)
new_points = (new_width, new_width)
rescaled_img = cv2.resize(image_, new_points, interpolation= cv2.INTER_LINEAR)

print(rescaled_img.shape)

# Display the result
plt.figure(figsize=(8, 6))

plt.imshow(rescaled_img)
plt.title("Resized Image")
plt.show()
```

<figure><img src="../../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>
