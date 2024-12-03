# Adding Noise to image

* Training data which we scrap from internet which will be HD, but in real life we dont get such images
* So we need to add noise to images to replicate real world situation

```python
image = cv2.imread('./data/beach-blue.jpg')

noise = np.random.normal(80, 150, image.shape)
noisy_image = image + noise
noisy_image = np.clip(noisy_image, 0, 255).astype(np.uint8)

noisy_image = cv2.cvtColor(noisy_image, cv2.COLOR_BGR2RGB)

plt.imshow(noisy_image)
plt.title("Noisy Image")
plt.show()
```

<figure><img src="../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>
