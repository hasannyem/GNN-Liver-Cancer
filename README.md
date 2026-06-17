# GNN-Based Cross-Modality Transfer Learning for Liver Cancer Classification

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)](https://pytorch.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📌 Overview

This repository contains the official implementation of:

**"Graph Neural Network-Based Cross-Modality Transfer for Liver Cancer Classification across Heterogeneous CT and MRI Imaging Domains"**

**Authors:** Md Nyem Hasan Bhuiyan, Rana Muhammad Zain Ul Abideen, Naveed Anwer Butt, Imran Ashraf, Daniel Gavilanes, Manuel Masias Vergara

---

## 🔬 Framework

The proposed framework performs cross-modality transfer learning using:
- **Swin Transformer** and **ResNet-50** backbones for 1024/2048-dim imaging embeddings
- **Patient Similarity Graph** construction using KNN (k=3,5,10) and Cosine similarity (τ=0.95, 0.99)
- **GATv2** (3-layer, 4-head Graph Attention Network v2) for 5-class liver cancer classification
- **Inductive learning** with 5-fold stratified cross-validation

---

## 📊 Datasets

| Dataset | Modality | Samples | Source |
|---|---|---|---|
| LiTS17 (CT) | CT Imaging | 130 scans / 58,638 slices | [Kaggle](https://www.kaggle.com/datasets/andrewmvd/lits-png) |
| MRI Multiclass | MRI Imaging | 11,992 images / 5 classes | [Kaggle](https://www.kaggle.com/datasets/ucimachinelearning/liver-cancer-multiclass-dataset) |

---

## 🏆 Results

| Configuration | Accuracy | Macro F1 | AUC-ROC |
|---|---|---|---|
| MRI-only (GATv2 KNN k=5) | 99.17% | 99.16% | 99.95% |
| CT+MRI Cross-modality (GATv2 KNN k=5, Swin) ★ | 99.28% | 99.28% | 99.98% |
| CT+MRI Cross-modality (GATv2 KNN k=5, ResNet) | 99.22% | 99.22% | 99.98% |

---

## 📁 Repository Structure

```
GNN-Liver-Cancer/
├── GNN_Liver_Swin_Base.ipynb        # Swin Transformer backbone pipeline
├── GNN_Liver_ResNet50.ipynb         # ResNet-50 backbone pipeline
├── GNN_Liver_Result_Analysis.ipynb  # Result analysis, figures, tables
├── README.md
└── LICENSE
```

---

## 🚀 How to Run

**1. Mount Google Drive and set paths (Cell 1-4)**

**2. Feature Extraction:**
- Cell 7: CNN backbone (Swin/ResNet)
- Cell 8: MRI embedding extraction
- Cell 9: CT embedding extraction

**3. Graph Construction:**
- Cell 10: Patient similarity graph (KNN/Cosine)

**4. GATv2 Training:**
- Cell 13-13e: Train all configurations

**5. Result Analysis:**
- Open `GNN_Liver_Result_Analysis.ipynb`
- Run all cells sequentially

---

## ⚙️ Requirements

```
torch>=2.0
torch-geometric
timm
scikit-learn
numpy
pandas
matplotlib
joblib
xgboost
shap
```

Install:
```bash
pip install torch torch-geometric timm scikit-learn numpy pandas matplotlib joblib xgboost shap
```

---

## 📄 Citation

If you use this code, please cite our paper:

```bibtex
@article{bhuiyan2025gnn,
  title={Graph Neural Network-Based Cross-Modality Transfer for Liver Cancer Classification across Heterogeneous CT and MRI Imaging Domains},
  author={Bhuiyan, Md Nyem Hasan and Abideen, Rana Muhammad Zain Ul and Butt, Naveed Anwer and Ashraf, Imran and Gavilanes, Daniel and Vergara, Manuel Masias},
  journal={},
  year={2025}
}
```

---

## 📬 Contact

**Md Nyem Hasan Bhuiyan** — Lead Author  
For questions or collaborations, please open an issue on this repository.

---

*For research purposes only. Not for clinical use.*
