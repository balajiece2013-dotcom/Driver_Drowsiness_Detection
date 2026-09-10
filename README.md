# Driver Drowsiness Detection using Eye Closure and Yawning Analysis with Deep Learning

## Project Overview

Driver fatigue and drowsiness can reduce alertness, reaction time, and decision-making ability, increasing the risk of road accidents.

This project develops a vision-based driver drowsiness detection system using facial images and deep learning. The system classifies facial images into four states:

- Closed
- Open
- no_yawn
- yawn

The four-class predictions are then converted into three fatigue levels:

- **Level 0 — Alert**
- **Level 1 — Mild Fatigue**
- **Level 2 — Severe Fatigue**

Two deep learning approaches are implemented and compared:

- Custom CNN
- MobileNetV2 Transfer Learning

## Dataset

The dataset contains **2,900 facial images** across four classes.

| Class | Images |
|---|---:|
| Closed | 726 |
| Open | 726 |
| no_yawn | 725 |
| yawn | 723 |
| **Total** | **2,900** |

The dataset was freshly divided into:

- Training: 2,029 images
- Validation: 435 images
- Test: 436 images

The original dataset was preserved, and the final implementation uses a fresh train-validation-test split.

## Preprocessing

Images are:

- Resized to 224 × 224 pixels
- Normalized to the range 0–1

Training data augmentation includes:

- Rotation
- Zoom
- Brightness variation
- Horizontal flipping

Validation and test images are only normalized.

## Models

### Custom CNN

A four-class Custom CNN was developed using convolutional layers, max pooling, a dense layer, dropout, and a softmax output layer.

### MobileNetV2

MobileNetV2 pretrained on ImageNet is used for transfer learning. The pretrained base is frozen and a custom classification head is added.

## Results

| Model | Test Accuracy | Precision | Recall |
|---|---:|---:|---:|
| Custom CNN | 81.19% | 81.32% | 81.19% |
| MobileNetV2 | 87.61% | 90.08% | 87.61% |

MobileNetV2 achieved better overall performance on the unseen test dataset.

## Fatigue Decision Logic

The predicted facial states are mapped to fatigue levels using rule-based logic:

| Predicted State | Fatigue Level |
|---|---|
| Open | Alert |
| no_yawn | Alert |
| yawn | Mild Fatigue |
| Closed | Severe Fatigue |

## Project Workflow

```text
Dataset
   ↓
EDA & Data Quality Analysis
   ↓
Preprocessing & Augmentation
   ↓
Train / Validation / Test Split
   ↓
Custom CNN
   ↓
MobileNetV2 Transfer Learning
   ↓
Model Evaluation
   ↓
Confusion Matrix & Performance Comparison
   ↓
Fatigue Decision Logic
   ↓
Fatigue Progression
   ↓
Final Drowsiness Result
