<div align="center">

# 🧠 Brain Tumor Detection & Localization with YOLOv11

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![YOLOv11](https://img.shields.io/badge/Model-YOLOv11-red.svg)](https://github.com/ultralytics/ultralytics)
[![PyTorch](https://img.shields.io/badge/Framework-PyTorch-orange.svg)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**A high-precision Medical AI pipeline for automated brain tumor detection in MRI scans.**

[Project Overview] • [Architecture] • [Training & Results] • [Usage]

</div>

---

## 📌 Project Overview
This project focuses on the intersection of Deep Learning and Medical Imaging. It provides an automated solution for detecting and localizing brain tumors from MRI (Magnetic Resonance Imaging) slices. By utilizing the latest **YOLOv11** architecture, the model ensures rapid inference without compromising the high accuracy required for clinical diagnostic support.

**Key Highlights:**
- **Medical Precision:** Fine-tuned to detect subtle anomalies in complex MRI textures.
- **Optimized for Speed:** Real-time detection capabilities suitable for integration into clinical workflows.
- **End-to-End Pipeline:** Covers everything from data preprocessing to visualization of results.

---

## ⚙️ Technical Architecture
The core of this system is built on the **YOLOv11** (You Only Look Once) framework, which treats object detection as a regression problem to spatially separated bounding boxes and associated class probabilities.

- **Base Model:** `yolo11n.pt` (Nano variant) for an optimal balance between parameter efficiency and accuracy.
- **Input Resolution:** Images are processed at **640x640** pixels to maintain spatial resolution for small tumor clusters.
- **Backend:** Developed using `ultralytics` and `PyTorch`.

---

## 📊 Training & Performance
The model was trained in a GPU-accelerated environment (NVIDIA Tesla T4) with the following configuration:

| Parameter | Value |
| :--- | :--- |
| **Epochs** | 100 |
| **Optimizer** | Auto-selected (AdamW/SGD) |
| **Batch Size** | Dynamic |
| **Confidence Threshold** | 0.25 (Inference) |

> **Results:** The model successfully learns to distinguish tumorous tissue from healthy brain structures, saving the optimal weights as `best_brain_tumor_detector.pt` for deployment.

---

## 🚀 Quick Start & Usage

### 1. Prerequisites
```bash
pip install ultralytics opencv-python matplotlib
```
### 2. Inference
To run detection on a new MRI scan, use the following snippet:
```
Python
from ultralytics import YOLO
import cv2

# Load the trained model
model = YOLO('best_brain_tumor_detector.pt')

# Run inference
results = model.predict(source='path_to_mri_image.jpg', conf=0.25)

# Visualize
results[0].show()
```
---

## 🖼️ Sample Results

---

## ⚖️ Disclaimer
This project is intended for research and educational purposes only. It is not a certified medical device and should not be used for clinical diagnosis without professional medical supervision.
