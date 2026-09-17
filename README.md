# Cancer Metastasis Detection from Histopathology Images

## Overview

This project focuses on detecting cancer metastasis from histopathology images using deep learning. A FastAI-based image classification pipeline was developed to classify microscopic tissue images into **Negative** and **Tumor** classes.

The project uses a **DenseNet169** architecture with transfer learning and includes image preprocessing, data augmentation, model fine-tuning, evaluation, and Grad-CAM-based visualization for model interpretability.

## Objectives

- Classify histopathology images as **Tumor** or **Negative**.
- Develop a deep learning pipeline for microscopic tissue image classification.
- Improve model performance through fine-tuning and hyperparameter optimization.
- Analyze model predictions using visual interpretability techniques.

## Dataset

The project uses histopathology images with a resolution of **96 × 96 pixels**.

The images are divided into two classes:

- **Negative** – non-tumor tissue
- **Tumor** – tissue containing metastatic tumor regions

The dataset is divided into training and validation sets using a stratified split to maintain class representation.

## Methodology

### 1. Image Preprocessing

The images are loaded and converted from BGR to RGB format using OpenCV. A custom image-loading pipeline is implemented to preprocess the histopathology images before training.

Image transformations include:

- Random rotations
- Horizontal and vertical flips
- Image shifting
- Brightness and contrast adjustments
- Cropping to the required input size

### 2. Model Architecture

A **DenseNet169** model pretrained on ImageNet is used as the backbone for image classification.

The model is implemented using:

- FastAI
- PyTorch
- DenseNet169
- Transfer learning

The model is initially trained with the pretrained layers and subsequently fine-tuned by unfreezing the network.

### 3. Training

The model is trained using the **One Cycle Policy** with different learning rates and weight-decay configurations.

Hyperparameter tuning and validation analysis are used to improve the model's performance.

### 4. Model Evaluation

The trained model is evaluated using:

- Accuracy
- Confusion Matrix
- ROC Curve
- AUC

The notebook records a validation **ROC-AUC of 0.9944**.

### 5. Model Interpretability

**Grad-CAM (Gradient-weighted Class Activation Mapping)** is implemented to visualize the regions of histopathology images that contribute to the model's predictions.

This provides visual insight into which parts of the tissue image the model considers important when predicting the presence of tumor tissue.

## Results

| Metric | Result |
|---|---:|
| Validation ROC-AUC | **0.9944** |
| Image Size | **96 × 96 pixels** |
| Model | **DenseNet169** |
| Framework | **FastAI / PyTorch** |
| Classes | **Negative, Tumor** |

The confusion-matrix analysis also shows a reduction in false-positive predictions after model fine-tuning compared with the earlier model stage.

## Technologies Used

- **Python**
- **FastAI**
- **PyTorch**
- **TensorFlow**
- **OpenCV**
- **NumPy**
- **Pandas**
- **Scikit-learn**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**

## Project Workflow

```text
Histopathology Images
        ↓
Image Preprocessing
        ↓
Data Augmentation
        ↓
Train / Validation Split
        ↓
DenseNet169 + Transfer Learning
        ↓
One Cycle Training
        ↓
Fine-Tuning
        ↓
Model Evaluation
        ↓
ROC-AUC / Confusion Matrix
        ↓
Grad-CAM Visualization
