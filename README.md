# Epilepsy Lesion Segmentation (FCD II Suite)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Dataset: OpenNeuro](https://img.shields.io/badge/Dataset-OpenNeuro%20ds004199-blue.svg)](https://openneuro.org/datasets/ds004199)
[![Status: Research / Graduation Project](https://img.shields.io/badge/Status-Graduation%20Project-purple.svg)](#overview)

<table style="width:100%; border:none; border-collapse:collapse;">
  <tr>
    <td style="width:50%; text-align:center; vertical-align:top; border:none; padding:10px;">
      <a href="./SynthFCD">
        <img src="https://github.com/user-attachments/assets/31dabe94-59b1-4f44-bc43-af62ed7dd85d" alt="SynthFCD Pipeline" width="440">
      </a>
      <br>
      <b><a href="./SynthFCD">SynthFCD: Synthetic Lesion Generation Pipeline</a></b>
    </td>
    <td style="width:50%; text-align:center; vertical-align:top; border:none; padding:10px;">
      <a href="./nnU-FCD">
        <img src="https://raw.githubusercontent.com/YassienTawfikk/nnU-FCD/main/figures/nnU-Net%20PIPELINE.png" alt="nnU-FCD Pipeline" width="440">
      </a>
      <br>
      <b><a href="./nnU-FCD">nnU-FCD: Supervised 3D nnU-Net Pipeline</a></b>
    </td>
  </tr>
</table>
An end-to-end deep learning framework and umbrella repository for **Focal Cortical Dysplasia (FCD Type II) Lesion Synthesis and Segmentation in 3D FLAIR MRI**. 

This super repository integrates two independent research pipelines developed as part of this graduation project via Git Submodules, covering both synthetic data generation from anatomical label maps and state-of-the-art 3D medical image segmentation using nnU-Net.

---

## 🏆 IEEE EMBC Finalist Recognition (`nnU-FCD`)

We are proud to announce that the **[nnU-FCD](./nnU-FCD)** branch of our graduation project—*Evaluation of nnU-Net for FCD II Lesion Segmentation in FLAIR MRI*—has been selected as an **IEEE EMBC Finalist**!

<p align="center">
  <img src="https://github.com/user-attachments/assets/0a2cb845-cf18-4833-98ee-b8d56bcdaef0" alt="IEEE Finalist Recognition" width="75%">
</p>

---

## 🎓 Graduation Defense & Video Presentation

We invite you to watch our full graduation project defense video presentation and review our final slide deck:

<p align="center">
  <a href="https://youtu.be/r8zxcXHgXfw?si=6211Zq6YrOgrMYU7">
    <img src="https://img.youtube.com/vi/r8zxcXHgXfw/maxresdefault.jpg" alt="Watch the Graduation Project Defense Video" width="90%">
  </a>
  <br>
  <em>▶ <a href="https://youtu.be/r8zxcXHgXfw?si=6211Zq6YrOgrMYU7">Click the thumbnail above to watch the full graduation project video presentation on YouTube</a></em>
</p>

* **📄 Presentation Slide Deck**: View and download our complete defense presentation: **[`presentation/GP_Final_Defense_FCD_Segmentation.pdf`](./presentation/GP_Final_Defense_FCD_Segmentation.pdf)**
* **🎥 Video Presentation Link**: [Watch on YouTube (`youtu.be/r8zxcXHgXfw`)](https://youtu.be/r8zxcXHgXfw?si=6211Zq6YrOgrMYU7)

---

## 🏛️ Repository Architecture & Submodules

This repository is structured as a **Super Repository** containing two linked submodules alongside our defense materials:

```text
Epilepsy-Lesion-Segmentation/
├── .gitmodules           # Submodule configuration linking remote repositories
├── README.md             # This overview documentation
├── presentation/         # Final defense presentation slide deck (PDF)
├── SynthFCD/             # Submodule: Synthetic Data Generation Pipeline
└── nnU-FCD/              # Submodule: nnU-Net v2 Evaluation & Segmentation Pipeline
```

### 1. [SynthFCD](./SynthFCD)
**Synthetic Data Generation for FCD II Lesion Segmentation in FLAIR MRI**  
An active exploratory research pipeline investigating whether data scarcity bottlenecks in FCD lesion segmentation can be overcome by generating synthetic training images on-the-fly from anatomical label maps (`SynthSeg`-derived domain randomization). 

> **Current Status**: `SynthFCD` currently does **not** outperform the supervised `nnU-FCD` baseline and does not yet have an associated published paper. It is released as a complete, reproducible pipeline alongside an honest analysis of generative lesion realism and transfer mechanics.

* **Key Features**: On-the-fly 3D lesion synthesis, label map deformation, domain randomization, zero-real-data training pipeline.
* **Remote Repository**: [github.com/YassienTawfikk/SynthFCD](https://github.com/YassienTawfikk/SynthFCD)

---

### 2. [nnU-FCD](./nnU-FCD) *(IEEE EMBC Finalist & Official Paper Implementation)*
**Evaluation of nnU-Net for FCD II Lesion Segmentation in FLAIR MRI**  
The official PyTorch implementation, evaluation framework, and **IEEE EMBC Finalist** research paper addressing automated FCD Type II lesion detection. By incorporating radiological feature-based oversampling (`BSL + OVS + Aug`) and extensive domain augmentations on the standard Bonn FCD II dataset, `nnU-FCD` advances validation performance from `0.45` to `0.56` Pseudo Dice and establishes a reproducible benchmark.

* **Key Features**: Official IEEE EMBC paper implementation, radiological feature oversampling, `nnU-Net v2` pre-processing/training, pre-trained checkpoints.
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
