***

# Structure-Aware Learnable Multi-Scale Attention for Retinal Vessel Analysis

This repository contains the official **PyTorch implementation** of the paper:  
**"Structure-Aware Learnable Multi-Scale Attention for Retinal Vessel Analysis"**.

We propose a novel **Learnable Multi-Scale Attention (LMSA)** module and a **Multi-Task Learning (MTL)** framework to enhance vessel connectivity and segmentation accuracy in fundus imaging.
**LMSA Architecture (UNet + LMSA + MTL)**  
![Architecture](images/net.jpg)

**LMSA Architecture (Module Design)** 
![LMSA](images/lmsa.jpg)


## 1. Repository Structure

    LMSA_TMI_Official
    ├── .gitignore
    ├── images
    │   ├── Impact_of_lmsa.drawio.png
    │   ├── LMSA.drawio.png
    │   ├── ROC.png
    │   ├── unet_lmsa_mtl.png
    │   └── redlesion1.drawio.png
    ├── codes
    │   ├── attunet_train.py
    │   ├── cs2net_train.py
    │   └── unet_train.py.py
    ├── requirements.txt
    └── utils
        ├── organise_datasets.py
        └── statistical_significance.py

***

## 2. Getting Started

### 2.1 Installation

```bash
pip install -r requirements.txt
```

### 2.2 Automated Dataset Preparation

To ensure training scripts is stand alone so Got to the respective and download raw dataset files of DRIVE, CHASE_DB1 and STARE
Place raw downloads into a folder named `data`, then run:

```bash
python utils/organise_datasets.py
```
This script:

*   Decompresses raw files
*   Standardizes all images to `.png`
*   Generates required Train/Test splits


### 2.3 Expected Output Structure:

    DATASETS
    ├── DRIVE_dataset
    ├── Chase_DB1
    └── stare

***
## 3. Reproducing Paper Experiments

### 📊 **Architecture Generalization (Table III)**

To reproduce the cross-model benchmarks for all 8 backbones, execute the respective scripts from the root directory:

# 1. U-Net + LMSA + MTL
python3 `codes/unet_train.py`

# 2. Attention U-Net + LMSA + MTL
python3 `codes/attunet_train.py`

# 3. CS2-Net + LMSA + MTL
python3 `codes/cs2net_train.py`
***

### 📊 **Main Ablation Study (Table VII)**

Modify config settings at the top of `codes/unet_train.py`.  
Official evidence archived in `RESULTS/Ablation_study/`.

| Experiment | ID | Config Settings       | Mapping Folder                          |
| ---------- | -- | --------------------- | --------------------------------------- |
| Baseline   | A1 | LMSA=False, MTL=False | A1\_U-Net+Structural Losses\_(Baseline) |
| LMSA Only  | A2 | LMSA=True, MTL=False  | A2\_U-Net+LMSA\_no\_heads               |
| MTL Only   | A3 | LMSA=False, MTL=True  | A3\_U-Net+Aux\_Heads\_no\_LMSA          |
| Proposed   | A4 | LMSA=True, MTL=True   | A4\_LMSA\_3\_Heads                      |

***

### 📊 **Scale Sensitivity Analysis (Table VIII)**

Adjust `LMSA_K` (number of scales) in training scripts.  
## 4. Results

- **Performance Impact**  
  ![Performance Impact](images/Impact_of_lmsa_sr.jpg)

- **ROC Curves**  
  ![ROC Curves](images/ROC_AUC_Enhanced_Zoom 1.png)

- **Complex situvation**  
  ![Complex situvation](images/Complex_situvation.jpg)

- **Pathological Robustness**  
  ![Pathological Robustness](images/redlesion1.jpg)

***

## 5. Technical References & Acknowledgments
*   **CS2-Net**: <https://github.com/moucheng/CS2-Net>
*   **Attention U-Net**: <https://github.com/ozan-oktay/Attention-Gated-Networks>
*   **U-Net**: <https://github.com/milesial/Pytorch-UNet>

***


## 6. Contact

For technical queries, bug reports, or reproducibility issues:

Developer Contact: chandan.v1@tataelxsi.co.in
***

