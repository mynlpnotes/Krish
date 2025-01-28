# Coding - ResNet - Pretrained

* Pytorch accepts either tensor or PIL image, so we need to use PIL
* Different timings:
  * Preprocessing timing
  * Inference timing
  * Post processing timing (From index getting class name etc.)
* If we do pretrained = false ⇒ Weights wont be downloaded
* We will also have approach in which we will download the weights, we wont train convolution layers to train, we will only train fully connected network
* Transfer learning: minimal adjustment to model weights
* Fine tuning: model is already trained, update features, fully connected layer

```python
import torch
import torchvision.models as models
import torchvision.transforms as transforms
from PIL import Image

resnet34 = models.resnet34(pretrained=True)

# Since we using pretrained model, so we dont need to train
# resnet34.train()
resnet34.eval()

transform = transforms.Compose([
    transforms.Resize((224,224)),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
])

!wget https://raw.githubusercontent.com/pytorch/hub/master/imagenet_classes.txt

image_path = "/content/car.jpg"
image = Image.open(image_path).convert("RGB")

input_tensor_image = transform(image).unsqueeze(0)

with torch.no_grad():
  outputs = resnet34(input_tensor_image)

  _, predicted_class = outputs.max(1)
  print(f"Predicted class index : {predicted_class.item()}")
  # Predicted class index : 817
  
  with open("/content/imagenet_classes.txt") as f:
  labels = [line.strip() for line in f.readlines()]

print(f"Predicted class index : {labels[predicted_class.item()]}")
# Predicted class index : sports car
```
