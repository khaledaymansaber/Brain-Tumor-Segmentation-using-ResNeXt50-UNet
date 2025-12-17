# 🧠 Brain Tumor Segmentation using ResNeXt50-UNet

This project focuses on **brain tumor segmentation** from MRI images using a **U-Net architecture with a ResNeXt50 encoder**.  
The model is trained and evaluated on the **LGG Brain MRI Segmentation Dataset**.

---

## 📌 Project Overview

- **Task**: Binary image segmentation (Tumor / Background)
- **Dataset**: LGG Brain MRI Segmentation Dataset
- **Architecture**: ResNeXt50 Encoder + U-Net Decoder
- **Framework**: PyTorch
- **Input Size**: 256 × 256
- **Loss Function**: BCE + Dice Loss
- **Evaluation Metrics**: Dice Coefficient, Mean IoU

---

## 📂 Dataset Preparation

- MRI images and their corresponding binary masks are loaded and matched correctly.
- Each sample consists of:
  - Original MRI image
  - Ground truth tumor mask
- Stratified splitting is used to preserve class distribution.

### 🔹 Dataset Split
| Set        | Percentage |
|-----------|------------|
| Training  | ~76.5% |
| Validation| 10% |
| Testing   | ~13.5% |

---

## 🔄 Data Augmentation

To improve generalization and reduce overfitting, strong augmentations were applied using **Albumentations**:

- Random Resized Crop
- Horizontal & Vertical Flip
- Random Rotation (90°)
- Shift / Scale Transformations
- Elastic & Grid Distortion
- Brightness & Contrast Adjustment
- Normalization
- Conversion to Tensor

---

## 🏗 Model Architecture

### 🔹 ResNeXt50-UNet

- **Encoder**: Pretrained ResNeXt50
- **Decoder**: U-Net style upsampling blocks
- **Skip Connections**: Preserve spatial information
- **Output**: Binary segmentation mask (Sigmoid activation)

---

## ⚙️ Training Details

- **Optimizer**: Adam (lr = 5e-4)
- **Batch Size**: 26
- **Epochs**: Up to 20
- **Early Stopping**: Patience = 5
- **Best Model Saved Automatically**

---

## 📈 Training Results (Validation)

### 🔹 Best Validation Performance
- **Best Validation Dice Score**: **0.9516**
- **Best Epoch**: **Epoch 10**
- **Early Stopping Triggered**: Epoch 15
- **Saved Model**: `best_ResNeXt50.pth`

### 🔹 Training Log Snapshot
```text
Epoch [10/20] - Train Loss: 0.1256
Train DICE: 0.8877
Val DICE: 0.9516  ✅ BEST

Epoch [15/20] - Train DICE: 0.8926
Val DICE: 0.9447
⏹ Early stopping triggered

