# Resize

```python
height, width, _ = image.shape

print(image.shape)

image_ = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
new_width = int(width/8)
new_height = int(height/8)
new_points = (new_width, new_height)
# new_points = (400, 400)
rescaled_img = cv2.resize(image_, new_points, interpolation= cv2.INTER_LINEAR)

print(rescaled_img.shape)

# Display the result
plt.figure(figsize=(12, 8))

plt.imshow(rescaled_img)
plt.title("Resized Image")
plt.show()
```

<figure><img src="../../.gitbook/assets/{789ADE82-B767-4FE4-8C57-37E90B588BA9}.png" alt=""><figcaption></figcaption></figure>
