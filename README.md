# Guiding Block Detection for Visually Impaired Navigation using YOLOv8

## Overview

This project develops a computer vision-based object detection system for recognizing guiding blocks (*tactile paving*) to support navigation assistance for visually impaired individuals.

The system utilizes the YOLOv8 object detection model to classify and detect five guiding block conditions in real-time. The project serves as the foundation for a future smart glasses navigation system powered by Raspberry Pi.

---

## Features

* Real-time guiding block detection
* Multi-class object detection
* YOLOv8n lightweight architecture
* Custom dataset collected from public facilities
* Dataset balancing and augmentation
* Raspberry Pi deployment ready
* Smart glasses integration (future development)

---

## Detection Classes

| Class      | Description                        |
| ---------- | ---------------------------------- |
| Straight   | Straight guiding block             |
| Left       | Left-turn guiding block            |
| Right      | Right-turn guiding block           |
| Damaged    | Damaged guiding block              |
| Obstructed | Guiding block blocked by obstacles |

---

## Dataset Collection

Dataset was collected from multiple public locations in Indonesia:

* Universitas Pancasila
* Bojonggede Station
* Margonda Sidewalk

Additional open-source data from Roboflow was merged to improve class balance.

### Initial Dataset Distribution

| Class      | Images |
| ---------- | ------ |
| Straight   | 1198   |
| Left       | 18     |
| Right      | 46     |
| Damaged    | 108    |
| Obstructed | 133    |

### After Balancing & Augmentation

| Class      | Images |
| ---------- | ------ |
| Straight   | 800    |
| Left       | 800    |
| Right      | 800    |
| Damaged    | 800    |
| Obstructed | 800    |

Total Dataset: **4,000 Images**

---

## Data Preprocessing Pipeline

```text
Dataset Collection
        │
        ▼
Data Annotation
        │
        ▼
Image Resizing (640x640)
        │
        ▼
Data Augmentation
        │
        ▼
Dataset Balancing
        │
        ▼
Train / Validation / Test Split
```

### Augmentation Techniques

* Horizontal Flip
* Rotation
* Brightness Adjustment
* Saturation Adjustment
* Noise Injection
* Blur
* Shadow Simulation

### Dataset Split

| Dataset    | Percentage |
| ---------- | ---------- |
| Training   | 80%        |
| Validation | 10%        |
| Testing    | 10%        |

---

## Model Architecture

This project uses **YOLOv8n (Nano)** because it is lightweight and suitable for future deployment on Raspberry Pi embedded systems.

### Hyperparameters

| Parameter     | Value   |
| ------------- | ------- |
| Model         | YOLOv8n |
| Epoch         | 100     |
| Batch Size    | 16      |
| Learning Rate | 0.001   |
| Image Size    | 640     |

---

## Evaluation Results

| Metric    | Score  |
| --------- | ------ |
| Accuracy  | 95.09% |
| Precision | 95.23% |
| Recall    | 95.14% |
| F1-Score  | 94.97% |

The model demonstrates strong classification performance across all guiding block classes with minimal confusion between left-turn and right-turn classes.

---

## Project Structure

```bash
guiding-block-detection-yolov8/
│
├── dataset/
│   ├── train/
│   ├── valid/
│   └── test/
│
├── notebooks/
│   └── guidingblock-detect.ipynb
│
├── models/
│   └── best.pt
│
├── results/
│   ├── confusion_matrix.png
│   ├── training_results.png
│   └── sample_predictions/
│
├── README.md
└── requirements.txt
```

---

## Installation

Clone repository:

```bash
git clone https://github.com/yourusername/guiding-block-detection-yolov8.git
cd guiding-block-detection-yolov8
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Training

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="dataset.yaml",
    epochs=100,
    imgsz=640,
    batch=16
)
```

---

## Inference

```python
from ultralytics import YOLO

model = YOLO("best.pt")

results = model.predict(
    source="image.jpg",
    conf=0.5
)
```

---

## Sample Results

Add prediction examples here:

```text
results/
└── sample_predictions/
```

Example:

* Straight Guiding Block Detection
* Left Turn Guiding Block Detection
* Right Turn Guiding Block Detection
* Damaged Guiding Block Detection
* Obstructed Guiding Block Detection

---

## Technologies Used

* Python
* YOLOv8
* Ultralytics
* OpenCV
* Albumentations
* Label Studio
* Google Colab
* Computer Vision
* Deep Learning

---

## Future Work

* Deploy model on Raspberry Pi
* Develop smart glasses prototype
* Integrate real-time camera input
* Implement audio navigation feedback
* Optimize inference performance
* Expand dataset diversity

---

## Author

**Fircan Ferdinand**

Bachelor Thesis Project

Universitas Pancasila

Indonesia
