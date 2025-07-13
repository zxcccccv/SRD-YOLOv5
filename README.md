# SRD-YOLOv5: Efficient Multi-Scale UAV Object Detection

##  Overview

**SRD-YOLOv5** is a lightweight and high-performance object detection framework, designed for robust and efficient detection of small objects in UAV remote sensing images. Based on YOLOv5n, our method introduces a novel multi-scale feature fusion strategy to tackle scale variations and preserve fine-grained target details in complex aerial scenes.

> **Key Highlights:**
>
> * **Multi-scale Feature Fusion:** Enhanced with MSFE and SSFF modules for rich context aggregation.
> * **Extremely Small Target Detection:** Dedicated high-res detection head for micro-scale objects.
> * **Decoupled Head:** Separate classification/regression for reduced conflict and better localization.
> * **Superior Results:** State-of-the-art accuracy and speed on VisDrone2019, RSOD, and NWPU VHR-10 datasets.

---

## 🏗️ Architecture

![](assets/srd-yolov5-architecture.png) <!-- 可放置你的框架结构图 -->

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

## 📝 Features

* **Scale Sequence Feature Fusion (SSFF):** Integrates hierarchical features using 3D convolutions to strengthen semantic and spatial info.
* **Multi-Scale Feature Extraction (MSFE):** Parallel extraction and aggregation from multiple scales.
* **ESTDL:** Specialized for targets smaller than 8x8 pixels, using a 160x160 output layer for high-res object clues.
* **Decoupled Head:** Improves learning of classification and regression by processing separately.

---

## 📈 Results

### 1. VisDrone2019 Dataset

| Model      | mAP\@0.5 (%) | Precision (%) | FPS | Params (M) |
| ---------- | ------------ | ------------- | --- | ---------- |
| YOLOv5n    | 28.8         | 36.4          | 98  | 1.77       |
| YOLOv8n    | 33.7         | 44.5          | 95  | 3.00       |
| SRD-YOLOv5 | **35.9**     | **45.6**      | 102 | 4.18       |

### 2. RSOD Dataset

| Model      | mAP\@0.5 (%) | Precision (%) | FPS |
| ---------- | ------------ | ------------- | --- |
| YOLOv5n    | 90.4         | 83.9          | 135 |
| SRD-YOLOv5 | **94.6**     | **90.6**      | 117 |

> More results (including NWPU VHR-10) are detailed in the [paper](./docs/PLOS_SRDYOLOV5_Manuscript.pdf).

---

## 📥 Getting Started

### 1. Install Dependencies

```bash
git clone https://github.com/yourname/SRD-YOLOv5.git
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

### 3. Training

```bash
python train.py --cfg configs/srd_yolov5.yaml --data configs/visdrone.yaml --device 0
```

### 4. Inference

```bash
python test.py --weights runs/exp/best.pt --source data/VisDrone2019/test/
```

---

## 📊 Ablation Study

| Model Variant | mAP\@0.5 | mAP\@0.5:0.95 | APS (Small) |
| ------------- | -------- | ------------- | ----------- |
| YOLOv5n       | 25.8     | 13.1          | 6.3         |
| +SSFF         | 31.2     | 17.1          | 6.5         |
| +MSFE         | 31.4     | 17.8          | 6.7         |
| +ESTDL        | **35.9** | **20.2**      | **8.8**     |

---

## 📚 Citation

If you use SRD-YOLOv5 in your research, please cite:

```bibtex
@article{lai2025srd-yolov5,
  title={Enhancing UAV Object Detection with an Efficient Multi-Scale Feature Fusion Framework},
  author={Delun Lai, Kai Kang, Ke Xu, Xuzhe Ma, Yue Zhang, Fengling Huang, Jishizhan Chen},
  journal={PLOS ONE},
  year={2025},
}
```

---

## 🤝 Acknowledgments

* This repo is inspired by [ultralytics/yolov5](https://github.com/ultralytics/yolov5) and [VisDrone](https://github.com/VisDrone/VisDrone-Dataset).
* Supported by UNSW, Monash, SJTU, UCL, and collaborators.

---

## 📬 Contact

For questions, contact [jishizhan.chen@ucl.ac.uk](mailto:jishizhan.chen@ucl.ac.uk)
Project maintained by [Your Name](mailto:your.email@domain.com)

---

如需进一步定制（如加速部署、ONNX/TensorRT指引、Jetson Nano移植说明等），可告知你的具体需求，我可以继续完善！
