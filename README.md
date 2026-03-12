***

# Structure-Aware Learnable Multi-Scale Attention for Retinal Vessel Analysis

This repository contains the official **PyTorch implementation** of the paper:  
**"Structure-Aware Learnable Multi-Scale Attention for Retinal Vessel Analysis"**.

We propose a novel **Learnable Multi-Scale Attention (LMSA)** module and a **Multi-Task Learning (MTL)** framework to enhance vessel connectivity and segmentation accuracy in fundus imaging.
**LMSA Architecture (UNet + LMSA + MTL)**  



## 1. Repository Structure

    LMSA_TMI_Official
    ├── codes
    │   ├── attunet_train.py
    │   ├── cs2net_train.py
    │   └── unet_train.py.py
    ├── requirements.txt
    └── utils
        └── organise_datasets.py

***

## 2. Getting Started

### 2.1 Installation

```bash
pip install -r requirements.txt
```

### 2.2 Expected Data Structure:

    DATASETS
    ├── DRIVE_dataset
    ├── Chase_DB1
    └── stare
    └── Read me

***
## 3. Reproducing Paper Experiments

### 📊 **Architecture Generalization (Table V)**

To reproduce the cross-model benchmarks for all 8 backbones, execute the respective scripts from the root directory:

# 1. U-Net + LMSA + MTL
python3 `codes/unet_train.py`

# 2. Attention U-Net + LMSA + MTL
python3 `codes/attunet_train.py`

# 3. CS2-Net + LMSA + MTL
python3 `codes/cs2net_train.py`
***

### 📊 **Main Ablation Study (Table VI)**

Modify config settings at the top of `codes/unet_train.py`.  
Official evidence archived in `RESULTS/Ablation_study/`.

| Experiment | ID | Config Settings       | Mapping Folder                          |
| ---------- | -- | --------------------- | --------------------------------------- |
| Baseline   | A1 | LMSA=False, MTL=False | A1\_U-Net+Structural Losses\_(Baseline) |
| LMSA Only  | A2 | LMSA=True, MTL=False  | A2\_U-Net+LMSA\_no\_heads               |
| MTL Only   | A3 | LMSA=False, MTL=True  | A3\_U-Net+Aux\_Heads\_no\_LMSA          |
| Proposed   | A4 | LMSA=True, MTL=True   | A4\_LMSA\_3\_Heads                      |

***

### 📊 **Scale Sensitivity Analysis (Table VII)**

Adjust `LMSA_K` (number of scales) in training scripts.  


## 4. Technical References & Acknowledgments
*   **CS2-Net**: <https://github.com/moucheng/CS2-Net>
*   **Attention U-Net**: <https://github.com/ozan-oktay/Attention-Gated-Networks>
*   **U-Net**: <https://github.com/milesial/Pytorch-UNet>

***


## 5. Contact

For technical queries, bug reports, or reproducibility issues:

Developer Contact: chandan.v1@tataelxsi.co.in
***

