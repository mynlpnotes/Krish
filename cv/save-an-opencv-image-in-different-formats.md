# 🟢 Save an OpenCV image in different formats

* JPEG - The value can be between 0 to 100, where 100 produces the highest quality and 0 produces the lowest quality.&#x20;
* PNG - The value can be between 0 to 9, where 9 produces the highest compression with more time to save images into the file.

```python
cv2.imwrite("./temp/imagecv_SAVE_100.jpg", image_rgb, [cv2.IMWRITE_JPEG_QUALITY, 100]) # By default is 95
cv2.imwrite("./temp/imagecv_SAVE_50.jpg", image_rgb, [cv2.IMWRITE_JPEG_QUALITY, 50])
cv2.imwrite("./temp/imagecv_SAVE_0.jpg", image_rgb, [cv2.IMWRITE_JPEG_QUALITY, 0])
cv2.imwrite("./temp/imagecv_SAVE.png", image_rgb) # bydefault, compression is set to 3
cv2.imwrite("./temp/imagecv_SAVE_0.png", image_rgb, [int(cv2.IMWRITE_PNG_COMPRESSION),0]) # bydefault, compression is set to 3
cv2.imwrite("./temp/imagecv_SAVE_9.png", image_rgb, [int(cv2.IMWRITE_PNG_COMPRESSION),9])
```
