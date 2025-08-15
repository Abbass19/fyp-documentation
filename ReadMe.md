YOLOv8 Model Training for Multi-Environment Vehicle Detection
Overview

This project focuses on training YOLOv8 object detection models across four distinct datasets, followed by the creation of a custom unified dataset to maximize model diversity and ensure robustness in various environments.

The goal is to develop a generalized detection model capable of high performance across multiple real-world conditions.

Methodology
1. Dataset Collection

4 separate datasets collected from diverse sources.

Each dataset originally contained different label structures and object counts.

2. Dataset Unification

To ensure compatibility and simplify the training process:

Labels were reduced from 10 to 4 classes in some datasets.

Labels were reduced from 8 to 4 in others.

This process is referred to as "Unification".

Both original-label models and unified-label models were trained for performance comparison.

3. Model Training

YOLOv8 was used for all training runs.

Training code saved for:

Each of the 4 individual datasets.

The unified dataset.

The custom final dataset (built for maximum diversity).

A benchmarking process was implemented to compare scores from multiple models.

4. Utilities

Custom code to clear GPU memory in case of runtime errors.

Repository Structure
.
├── notebooks/                # Jupyter notebooks for training and benchmarking
│   ├── train_dataset1.ipynb
│   ├── train_dataset2.ipynb
│   ├── train_dataset3.ipynb
│   ├── train_dataset4.ipynb
│   ├── train_unified.ipynb
│   ├── train_custom_final.ipynb
│   └── benchmark_models.ipynb
├── utils/
│   └── clear_gpu.py
├── datasets/                 # Dataset preparation scripts or samples
├── README.md
└── .gitignore

Results

Detailed metrics are available in the notebook outputs.

Precision, recall, and mAP compared between:

Original-label models

Unified-label models

Custom final dataset model

Full Report Submitted to MU :

[Full Report On Google Drive](https://docs.google.com/document/d/1wQlhH0jVUkl-7ocXJRutJdapFWHnq_fL/edit?usp=sharing&ouid=108265425555663361559&rtpof=true&sd=true)





## Custom Unified Dataset

This dataset is created to build a YOLOv8 model capable of detecting objects from **different heights and perspectives**.  
It focuses on **cars, trucks, buses, and people**, combining images from multiple sources.

### Sources & Image Count
| Dataset | Starting ID | Number of Images |
|---------|------------|----------------|
| VisDrone | 0 | 8,625 |
| Traffic Aerial Images for Vehicle Detection | 10,000 | 6,120 |
| Aerial Images Dataset | 20,000 | 2,708 |
| UAVDT_2024 | 30,000 | 12,548 |

**Total images:** ~29,641 (≈30K)  

### Dataset Split
| Split | Images | Percentage |
|-------|--------|------------|
| Train | 22,053 | 73.56% |
| Validation | 4,148 | 13.84% |
| Test | 3,780 | 12.61% |

### Object Instances
| Class | Instances |
|-------|----------|
| Car | 1,001,858 |
| Bus | 92,514 |
| Truck | 7,908 |
| **Total** | 1,102,280 |

- **Average Objects per Image:** 36.7  
- **Average Object Size (% of image area):** 0.211  
- **Small Objects (<5% area):** 11.18%  
- **Object Overlap (Mean IoU):** 99.89%  

**Annotation Format:** YOLOv8 (`class_id center_x center_y width height`)