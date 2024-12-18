# 🟢 Custom Filter

* <mark style="color:purple;background-color:purple;">**Based on central point it is increasing and based on neighboring points it is decreasing**</mark>
* <mark style="color:purple;background-color:purple;">**b, g, r = cv2.split() ⇒ to split the individual channels**</mark>
* <mark style="color:purple;background-color:purple;">**cv2.filter2D ⇒  apply filter to an image**</mark>
* <mark style="color:purple;background-color:purple;">**cv2.merge(r,g,b) ⇒ to combine r, g and b channels**</mark>

```python
kernel = np.array([[0, -1, 0],
                   [-1, 5, -1],
                   [0, -1, 0]])

rgb_image = cv2.imread("./data/beach-blue.jpg")

def apply_filter(image, filter, arrange="RGB"):
    b, g, r = cv2.split(image)
    b_new = cv2.filter2D(b, -1, filter)
    g_new = cv2.filter2D(g, -1, filter)
    r_new = cv2.filter2D(r, -1, filter)
    if arrange=="RGB":
        image_filtered = cv2.merge([r_new, g_new, b_new])
    if arrange=="BGR":
        image_filtered = cv2.merge([b_new, g_new, r_new])
    if arrange=="GBR":
        image_filtered = cv2.merge([g_new, b_new, r_new])
    return image_filtered

filtered_image_rgb = apply_filter(rgb_image, filter=kernel, arrange="RGB")
filtered_image_gbr = apply_filter(rgb_image, filter=kernel, arrange="GBR")
```

<figure><img src="../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>
