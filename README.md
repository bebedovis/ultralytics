# YOLO Grayscale Support 

This repository extends the functionalities of the ultralytics library by adding support for grayscale images. This functionality has been tested for detection and classification only. Its use for pose and segmentation haven't been tested yet lol.

## Installation

To use grayscale image functionality in YOLO, replace the default `ultralytics` package with the modified version from this repository.

**Using CLI**

Go to the python packages or anaconda env libraries:
```bash
cd /path/to/python/packages
```

Remove the ultralytics package and clone this repo:
```bash
rm -r ultralytics
git clone  git@github.com:Mauricio-Gonzalez-Ortiz/ultralytics.git
```

Extract the ultralytics folder:
```bash
find "ultralytics" -mindepth 1 -path "ultralytics/ultralytics" -prune -o -exec rm -rf {} +
mv ultralytics/ultralytics/* ultralytics/
rm -r ultralytics/ultralytics
```

**Editing your own package**

Follow the steps in this medium article: 

*lol haven't wirtten it*

### Training 

To train a model in python you just need to specify a configuration flag for the number of channels  "ch=1"

**Python Example**

```python
from ultralytics import YOLO

model = YOLO("yolov8.pt")
model.train(data="yaml_file.yaml", ..., ch=1)
```

**CLI Example** 

```bash 
yolo detect/classify train data=yaml_file_path/folder_path ... ch=1
```

### Prediction 

For prediction, it is recommended to specify the same "ch=1" flag 

**Python Example**
```python

from ultralytics import YOLO
import cv2 

model = YOLO("path/to/your/model.pt")
img = cv2.imread("path/to/your/image", cv2.IMREAD_GRAYSCALE) 
results = model(img, ch=1)
```

**CLI Example**

Currently, prediction on grayscale images using the CLI doesn't work. 
