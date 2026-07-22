# Epilepsy Lesion Segmentation (FCD II Suite)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Dataset: OpenNeuro](https://img.shields.io/badge/Dataset-OpenNeuro%20ds004199-blue.svg)](https://openneuro.org/datasets/ds004199)
[![Status: Research / Graduation Project](https://img.shields.io/badge/Status-Graduation%20Project-purple.svg)](#overview)

An end-to-end deep learning framework and umbrella repository for **Focal Cortical Dysplasia (FCD Type II) Lesion Synthesis and Segmentation in 3D FLAIR MRI**. 

This super repository integrates two independent research pipelines developed as part of this graduation project via Git Submodules, covering both synthetic data generation from anatomical label maps and state-of-the-art 3D medical image segmentation using nnU-Net.

---

## 🏛️ Repository Architecture & Submodules

This repository is structured as a **Super Repository** containing two linked submodules:

```text
Epilepsy-Lesion-Segmentation/
├── .gitmodules           # Submodule configuration linking remote repositories
├── README.md             # This overview documentation
├── SynthFCD/             # Submodule: Synthetic Data Generation Pipeline
└── nnU-FCD/              # Submodule: nnU-Net v2 Evaluation & Segmentation Pipeline
```

### 1. [SynthFCD](./SynthFCD)
**Synthetic Data Generation for FCD II Lesion Segmentation in FLAIR MRI**  
A PyTorch implementation of a `SynthSeg`-derived pipeline that trains a 3D U-Net to segment Focal Cortical Dysplasia lesions using FLAIR volumes synthesized on-the-fly from anatomical label maps. This branch enables robust model training without requiring real patient MRI volumes in the training set through domain randomization, Gaussian Mixture sampling, and simulated physics/artifact corruptions (bias field, gamma transformations, and noise).

* **Key Features**: On-the-fly 3D lesion synthesis, label map deformation, domain randomization, zero-real-data training pipeline.
* **Remote Repository**: [github.com/YassienTawfikk/SynthFCD](https://github.com/YassienTawfikk/SynthFCD)

---

### 2. [nnU-FCD](./nnU-FCD)
**Evaluation of nnU-Net for FCD II Lesions Segmentation in FLAIR MRI**  
The official PyTorch implementation and evaluation framework for training, tuning, and deploying state-of-the-art `nnU-Net v2` architectures specifically optimized for automated detection and segmentation of FCD Type II lesions.

* **Key Features**: Full `nnU-Net v2` pre-processing and training pipeline, evaluation metrics, visual analysis, and pre-trained model checkpoints.
* **Remote Repository**: [github.com/YassienTawfikk/nnU-FCD](https://github.com/YassienTawfikk/nnU-FCD)

---

## 🚀 Quick Start Guide

### Cloning the Super Repository
Because this repository uses Git Submodules, use the `--recursive` flag when cloning to automatically download the code inside both `SynthFCD` and `nnU-FCD`:

```bash
git clone --recursive https://github.com/YassienTawfikk/Epilepsy-Lesion-Segmentation.git
cd Epilepsy-Lesion-Segmentation
```

If you already cloned the repository without the `--recursive` flag, initialize and fetch the submodules manually:

```bash
git submodule update --init --recursive
```

---

## 🔄 Working with Submodules

### Pulling the Latest Changes across All Submodules
To pull the latest upstream changes from both submodule remotes simultaneously:

```bash
git submodule update --remote --merge
```

### Pushing Changes Made Inside a Submodule
If you make code modifications directly inside `./SynthFCD` or `./nnU-FCD`:
1. Navigate into the specific submodule directory (`cd SynthFCD` or `cd nnU-FCD`).
2. Commit and push your changes to that repository's remote (`git add . && git commit -m "update" && git push origin main`).
3. Return to the root super repository directory (`cd ..`).
4. Commit the updated submodule pointer (`git add SynthFCD && git commit -m "Update SynthFCD submodule pointer"`).

---

## 📊 End-to-End Workflow

1. **Synthesize & Pretrain**: Utilize `SynthFCD` to generate synthetic FCD lesions from anatomical label maps and train baseline segmentation models without patient privacy constraints.
2. **Segment & Evaluate**: Feed synthetic data or real patient validation cohorts (`OpenNeuro ds004199`) into `nnU-FCD` to benchmark and deploy top-performing 3D `nnU-Net v2` models.
