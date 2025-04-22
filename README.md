# YOLOv5-GhostNet-AFNO for UAV Object Detection

A lightweight, real-time UAV object detection framework based on YOLOv5 architecture, enhanced with GhostNet and Adaptive Fourier Neural Operator (AFNO 2D). This model is optimized for aerial surveillance tasks with improved small object detection, reduced GFLOPs, and increased FPS — making it ideal for deployment on resource-constrained devices like drones.

---

## Objectives of the Invention

- Develop a **lightweight, real-time** UAV detection system with high accuracy and low GFLOPs.
- Reduce computational complexity using **AFNO 2D** for frequency-aware feature extraction.
- Improve **small object detection** with Ghost Bottleneck and SPPF modules.
- Enhance multi-scale feature representation using **C3Ghost** and **DWConv**.
- Apply **robust data augmentation** (flip, mosaic, scale) to minimize false detections.

---
## Dataset used:

This project uses the drone-vs-bird Dataset provided by Roboflow Universe:

dam. drone-vs-bird Dataset. Roboflow Universe, Mar. 2023. Available at: https://universe.roboflow.com/dam-tpuul/drone-vs-bird-lanzg

---

## Working Principle

This project integrates GhostNet and AFNO 2D into a modified YOLOv5 framework to enhance detection in aerial imagery:

- **Backbone**:
  - GhostConv and GhostBottleneck reduce FLOPs while preserving features.
  - SPPF expands the receptive field to better detect small drones.
  - AFNO 2D processes feature maps in the frequency domain to capture long-range dependencies.

- **Neck**:
  - DWConv and C3Ghost modules optimize multi-scale feature fusion.
  - Enhanced top-down feature aggregation for improved object representation.

- **Head**:
  - Three-scale detection (P3/8, P4/16, P5/32).
  - Tailored anchor boxes and modified Detect module for precise bounding box regression.

---

## 📊 Experimental Results

| Model                          | GFLOPs | Params     | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 | FPS |
|-------------------------------|--------|------------|-----------|--------|---------|--------------|-----|
| YOLOv5s                       | 16.6   | 7.2M       | **89.0**      | **79.2**   | 79.0    | 42.7         | 48  |
| YOLOv5 + ShuffleNet + PEAM    | 6.9    | 4.28M      | 77.0      | 76.4   | 76.0    | 38.3         | 65  |
| YOLOv5 + MobileNet + PEAM     | 7.9    | 4.77M      | 80.0      | 78.5   | 78.0    | 38.6         | 57  |
| **YOLOv5 + GhostNet + AFNO (proposed)**  | **6.6**| **2.68M**  | 84.2  | 78.9| **80.4**| **42.8**     | **69** |

---

## Key Features

-  **GhostNet Backbone** — Efficient feature map generation with fewer parameters.
-  **AFNO 2D** — Global frequency-based feature enhancement.
-  **SPPF & C3Ghost** — Better receptive field and feature refinement.
-  **DWConv** — Efficient depthwise convolutions in the neck for fusion.
-  **Real-time FPS** — Achieves 69 FPS with 6.6 GFLOPs on UAV platforms.

- ![image](https://github.com/user-attachments/assets/3f5bd1a3-8f12-4e61-a86b-9a919e156fd5)


---

## 🛠 Installation

```bash
git clone https://github.com/kavinakash/yolov5_ghostnet_AFNO.git
cd yolov5_ghostnet_AFNO
pip install -r requirements.txt
```

