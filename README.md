# YOLOv8 Model Training for Multi-Environment Vehicle Detection

---

## 📝 Overview
This project trains **YOLOv8 object detection models** on **four distinct datasets** and a **custom unified dataset** to maximize model diversity and ensure robustness across different environments.  

The unified dataset combines **four different aerial vehicle detection datasets**, ensuring variety in environments, object sizes, and perspectives.

<p align="center">
  <img src="assests/data_composition.PNG" width="500"/>
</p>
<em>Figure 0 – Data composition from 4 sources.</em>

The goal is to build a **generalized detection model** capable of high performance in multiple real-world conditions.

---

## 📂 Dataset Composition
The unified dataset combines **four different aerial vehicle detection datasets**, ensuring variety in environments, object sizes, and perspectives.

![Dataset Composition](assests/data_composition.png)  
*Figure 0 – Data composition from 4 sources.*

---

## ⚙️ Methodology

### Dataset Unification
- Labels reduced to **4 consistent classes** across datasets.  
- Some datasets reduced from 10 → 4 classes.  
- Others reduced from 8 → 4 classes.  
- Both **original-label** and **unified-label** models were trained for comparison.

![Model Comparison](assests/model_comparison_unification.png)  
*Figure 2 – Model comparison before and after unification.*

---

### Model Training
- **YOLOv8** used for all experiments.  
- Training performed on:
  - 4 individual datasets  
  - Unified dataset  
  - Final custom dataset (for maximum diversity)  
- Extensive benchmarking for robustness evaluation.

![YOLOv8 Object Detection](assests/yolo_detection_example.png)  
*Figure 1 – Model applied to a single image (YOLOv8 object detection).*

---

### Special Experiments
- **YOLOv8 vs YOLOv8-OBB** tested on a sample dataset.  
- Cross-dataset benchmarking to measure generalization.

![YOLOv8 vs YOLOv8-OBB](assests/yolo_vs_obb.png)  
*Figure 3 – YOLOv8 vs YOLOv8-OBB on a sample image.*

![Cross-Dataset Benchmark](assests/cross_dataset_benchmark.PNG)  
*Figure 4 – Benchmark results of models tested outside their own datasets.*

---

### Model Interpretability
To understand decision-making, **Eigen-CAM heatmaps** were generated for detection outputs.

![Eigen-CAM Heatmap](assests/eigen_cam_heatmap.jpg)  
*Figure 5 – Eigen-CAM heatmap visualization.*

---

## 🛠 Utilities
- **GPU memory clearing script** to avoid CUDA memory errors during training.

---
### <a name="yolov8-vs-obb"></a>YOLOv8 vs YOLOv8-OBB Comparison
<p>
<strong>Objective:</strong> Evaluate how standard YOLOv8 compares with YOLOv8-OBB (Oriented Bounding Box) for detecting vehicles in aerial images.
</p>

<p>
<strong>Findings:</strong>
<ul>
  <li>YOLOv8-OBB can better localize objects with varying orientations.</li>
  <li>Standard YOLOv8 is faster but may miss rotated objects or partially occluded ones.</li>
  <li>Benchmarks showed a <strong>slight improvement in mAP</strong> for OBB on datasets with many rotated vehicles.</li>
</ul>
</p>

<p>
<strong>Conclusion:</strong> YOLOv8-OBB is preferred for datasets with highly rotated or angled objects, while standard YOLOv8 is sufficient for general detection.
</p>

<p align="center">
  <img src="assests/yolo_vs_obb.png" width="400"/>
</p>
<em>Figure 3 – Performance comparison between YOLOv8 and YOLOv8-OBB.</em>




## 📊 Results Summary
- Precision, Recall, and mAP compared between:
  - Original-label models
  - Unified-label models
  - Final custom dataset model  
- Detailed metrics available in training notebooks.

---

## 📁 Repository Structure

| Path         | Description |
|--------------|-------------|
| `notebooks/` | Jupyter notebooks for training & benchmarking |
| `utils/`     | GPU clearing and helper scripts |
| `datasets/`  | Dataset preparation scripts or samples |
| `assests/`    | Figures and visual results |
| `README.md`  | Project documentation |
| `.gitignore` | Ignored files configuration |

---

## 📄 Full Report
Full documentation and experiments submitted to **MU** 🙂
