# SRD-YOLOv5: Efficient Multi-Scale UAV Object Detection

The code will be released after paper acceptance.

##  Overview

**SRD-YOLOv5** is a lightweight and high-performance object detection framework, designed for robust and efficient detection of small objects in UAV remote sensing images. Based on YOLOv5n, our method introduces a novel multi-scale feature fusion strategy to tackle scale variations and preserve fine-grained target details in complex aerial scenes.

> **Key Highlights:**
>
> * **Multi-scale Feature Fusion:** Enhanced with MSFE and SSFF modules for rich context aggregation.
> * **Extremely Small Target Detection:** Dedicated high-res detection head for micro-scale objects.
> * **Decoupled Head:** Separate classification/regression for reduced conflict and better localization.
> * **Superior Results:** State-of-the-art accuracy and speed on VisDrone2019, RSOD, and NWPU VHR-10 datasets.

---

## Architecture
<img width="776" height="712" alt="image" src="https://github.com/user-attachments/assets/5b98503c-8c20-404b-af73-7fd22badf01d" />


* **Backbone:** YOLOv5n
* **Neck:** Multi-Scale Feature Fusion Layer (MSFE + SSFF)
* **Head:** Decoupled Head + Extremely Small Target Detection Layer (ESTDL)
* **Loss:** CIoU, Varifocal, and Distribution Focal Loss

---

## 📦 Directory Structure

```
SRD-YOLOv5/
├── configs/                 # Training and model configs
├── data/                    # Data loading, preparation scripts
├── models/                  # Model modules: backbone, neck, head
├── utils/                   # Common utilities
├── train.py                 # Training pipeline
├── test.py                  # Evaluation & inference
├── requirements.txt         # Environment requirements
└── README.md
```

---



## Getting Started

### 1. Install Dependencies

```bash
git clone https://github.com/zxcccccv/SRD-YOLOv5.git
cd SRD-YOLOv5
pip install -r requirements.txt
```

### 2. Prepare Datasets

* Download VisDrone2019: [https://github.com/VisDrone/VisDrone-Dataset](https://github.com/VisDrone/VisDrone-Dataset)
* Download RSOD: [https://github.com/RSIA-LIESMARS-WHU/RSOD-Dataset-](https://github.com/RSIA-LIESMARS-WHU/RSOD-Dataset-)
* Download NWPU VHR-10: [Google Drive](https://github.com/alanli2018/NWPU-VHR-10-dataset)

Organize folders as:

```
data/
 ├── VisDrone2019/
 ├── RSOD/
 └── NWPU-VHR-10/
```


