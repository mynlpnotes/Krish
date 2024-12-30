# Image DataLoader

* When working with image classification ⇒ Dog, Cat, Car, Bike (Labels)
* The folder structure will be
* Dataset
  * Dog ⇒ Dog1.jpeg, Dog2.jpeg
  * Cat ⇒ Cat.jpeg
  * Car&#x20;
  * Bike
* With the help of python we will write a script to divide the images into train, val, test for each folder
* ```python
  # This values have come from winning team of ImageNet, they 
  # found better results are given when this values are used
  transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
  ```

```python
import torch
from torch.utils.data import Dataset, DataLoader
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from torchvision import datasets, transforms
from PIL import Image

class ImageDataset(Dataset):
    def __init__(self, image_dir, transform=None):
        self.image_dir = image_dir
        self.transform = transform
        self.image_paths = []  # Store image file paths
        self.labels = []  # Store image labels

        # Load all image paths and their corresponding labels (class folder names)
        for label, class_dir in enumerate(os.listdir(image_dir)):  # Each folder is a class
            class_path = os.path.join(image_dir, class_dir)
            for img_name in os.listdir(class_path):
                self.image_paths.append(os.path.join(class_path, img_name))
                self.labels.append(label)

    def __len__(self):
        return len(self.image_paths)  # Returns the total number of images

    def __getitem__(self, idx):
        img_path = self.image_paths[idx]
        image = Image.open(img_path).convert("RGB")  # Load image and convert to RGB
        label = self.labels[idx]

        if self.transform:
            image = self.transform(image)

        return image, label

transform = transforms.Compose([
    transforms.Resize((128, 128)),  # Resize images to 128x128
    transforms.ToTensor(),  # Convert to tensor
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])  # Normalize
])

# Paths to the image datasets
train_image_dir = 'path/to/train'
val_image_dir = 'path/to/val'
test_image_dir = 'path/to/test'

# Create datasets
train_image_dataset = ImageDataset(image_dir=train_image_dir, transform=transform)
val_image_dataset = ImageDataset(image_dir=val_image_dir, transform=transform)
test_image_dataset = ImageDataset(image_dir=test_image_dir, transform=transform)

# Create DataLoaders
train_image_loader = DataLoader(dataset=train_image_dataset, batch_size=32, shuffle=True)
val_image_loader = DataLoader(dataset=val_image_dataset, batch_size=32, shuffle=False)
test_image_loader = DataLoader(dataset=test_image_dataset, batch_size=32, shuffle=False)

# Example: Iterating through batches of the train_image_loader
for images, labels in train_image_loader:
    print(images.shape, labels.shape)

import os
print(os.listdir("/content/sample_data"))

for idx, file_name in enumerate(os.listdir("/content/sample_data")):
  print(idx, file_name)
  print(os.path.join("/content/sample_data", file_name))
```
