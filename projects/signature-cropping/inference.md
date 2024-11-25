# Inference

* **Decode the base64 of image:**
  *

      ```python
              decoded_bytes = base64.b64decode(base64_string)
              np_array = np.frombuffer(decoded_bytes, np.uint8)
              cv_image = cv2.imdecode(np_array, cv2.IMREAD_COLOR)
      ```
* **Detect signature:**
  *

      ```python
      def predict(chosen_model, img, classes=[], conf=0.5):
          if classes:
              results = chosen_model.predict(img, classes=classes, conf=conf)
          else:
              results = chosen_model.predict(img, conf=conf)

      model = YOLO(model_path)
      results = predict(model, img, classes, conf=conf)
      ```
  * From the bounding boxes which we get, we will keep only that much part of the image
* **Enhance the image:**
  * **Make it gray scale**
  *

      ```python
      gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
      ```
  * **Use adaptive thresholding to make paper white and signature black**
  *

      ```python
      _, thresholded_image = cv2.threshold(
              deconvolution_gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU
          )
      ```
  * Apply CLAHE for further contrast enhancement
  *

      ```python
      clahe = cv2.createCLAHE(clipLimit=clip_limit, tileGridSize=tile_grid_size)
      ```
  * **Remove whitespace**
  *

      ```python
      def remove_white_space(image):
          import cv2
          
          blur = cv2.GaussianBlur(image, (25,25), 0)
          thresh = cv2.threshold(blur, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)[1]
          noise_kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (3,3))
          opening = cv2.morphologyEx(thresh, cv2.MORPH_OPEN, noise_kernel, iterations=2)
          close_kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (7,7))
          close = cv2.morphologyEx(opening, cv2.MORPH_CLOSE, close_kernel, iterations=3)
      # Find enclosing boundingbox and crop ROI\n”,
          coords = cv2.findNonZero(close)
          x,y,w,h = cv2.boundingRect(coords)
          return image[y:y+h, x:x+w]
      ```
  * **Rotate the image:**
  *

      ```python
      def rotate_image(image):
          import cv2
          height, width = image.shape

          if height > width:
              rotated_image = cv2.rotate(image, cv2.ROTATE_90_CLOCKWISE)
              return rotated_image
          else:
              return image
      ```
  * **Resize the image:**
  *

      ```python
      import cv2
      import numpy as np

      def resize_image(image, config):
          target_width = config['width']
          target_height = config['height']

          # Get the original dimensions
          original_height, original_width = image.shape[:2]

          # Calculate the aspect ratio
          aspect_ratio = original_width / original_height

          # Calculate the new dimensions while maintaining the aspect ratio
          new_width = int(np.round(target_height * aspect_ratio))
          new_height = int(np.round(target_width / aspect_ratio))

          # Choose the dimensions that fit within the target size
          if new_width <= target_width:
              resized_width, resized_height = new_width, target_height
          else:
              resized_width, resized_height = target_width, new_height

          # Resize the image and explicitly cast to np.uint8
          resized_image = np.uint8(cv2.resize(image, (resized_width, resized_height)))

          # Create a blank canvas of the target size
          canvas = np.zeros((target_height, target_width), dtype=np.uint8)
          canvas = np.ones((target_height, target_width), dtype=np.uint8) * 255

          # Calculate the position to paste the resized image in the center
          x_offset = (target_width - resized_width) // 2
          y_offset = (target_height - resized_height) // 2

          # Paste the resized image onto the canvas
          canvas[y_offset:y_offset + resized_height, x_offset:x_offset + resized_width] = resized_image

          #cv2.imwrite('Downloaded Image.jpg', canvas)
          return canvas

      ```
* **Encode the image back into base64:**
  *

      ```python
          _, img_encoded = cv2.imencode('.jpg', image)
          base64_encoded = base64.b64encode(img_encoded).decode('utf-8')
      ```

