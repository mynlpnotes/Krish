# 🟢 Reading from video stream

```python
import cv2

cam_webcam = cv2.VideoCapture(0) # default webcam
# cam_file = cv2.VideoCapture("./data/video.mp4") # default webcam

while True:
    ret, frame = cam_webcam.read()

    # ret, frame = cam_file.read()

    if not ret:
        break

    cv2.imshow("Video webcam", frame)
    # Simple hack
    # cv2.imwrite("./data/temp.jpg", frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cam_webcam.release()
cv2.destroyAllWindows()
```
