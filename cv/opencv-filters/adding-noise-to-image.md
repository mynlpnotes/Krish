# Adding Noise to image

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

<figure><img src="../../.gitbook/assets/{6F58DCA7-1D7C-4089-A68F-9BE10AB9DF2C}.png" alt=""><figcaption></figcaption></figure>
