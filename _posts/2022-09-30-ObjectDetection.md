---
toc: true
layout: post
comments: true
description: Some quick notes on Object Detection
categories: [markdown, tech]
title: Object Detection using YOLOv5
---

# Introduction
Repository: <https://github.com/Ian729/yolov5>  
Dataset: <https://cocodataset.org/#home>  
Dataset Categories: <https://gist.github.com/SrikarNamburu/0945de8f9a8714ec245dde3443e9d487>  

# Installation
```bash
git clone https://github.com/Ian729/yolov5  # clone
cd yolov5
pip install -r requirements.txt  # install
```

# Usage
## Inference with detect.py
detect.py runs inference on a variety of sources, downloading models automatically from the latest YOLOv5 release and saving results to runs/detect.
```python
python detect.py --source 0  # webcam
                          img.jpg  # image
                          vid.mp4  # video
                          screen  # screenshot
                          path/  # directory
                          'path/*.jpg'  # glob
                          'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                          'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```

## Inference
YOLOv5 PyTorch Hub inference. Models download automatically from the latest YOLOv5 release.
```python
import torch

# Model
model = torch.hub.load('ultralytics/yolov5', 'yolov5s')  # or yolov5n - yolov5x6, custom

# Images
img = 'https://ultralytics.com/images/zidane.jpg'  # or file, Path, PIL, OpenCV, numpy, list

# Inference
results = model(img)

# Results
results.print()  # or .show(), .save(), .crop(), .pandas(), etc.
```