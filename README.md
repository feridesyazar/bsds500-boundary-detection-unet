# 🐻 BSDS500 Boundary Detection with U-Net

## Project Overview

This project presents an approach to image boundary detection using the **Berkeley Segmentation Dataset 500 (BSDS500)** and a compact **U-Net convolutional neural network**.

The objective is to learn pixel-level boundary patterns from natural images and generate boundary maps for unseen images.

The workflow includes data preparation, ground-truth boundary processing, visualization, U-Net modeling, training, validation, evaluation, prediction, and model saving.

---

## Dataset

The **BSDS500 dataset** contains 500 natural images with multiple human-generated segmentation annotations.

| Dataset Split | Images |
| --- | ---: |
| Training | 200 |
| Validation | 100 |
| Test | 200 |
| **Total** | **500** |

The images and corresponding boundary annotations were resized to **128 × 128 pixels** for model training.

Dataset source:

[BSDS500 - Berkeley Segmentation Dataset 500 on Kaggle](https://www.kaggle.com/datasets/balraj98/berkeley-segmentation-dataset-500-bsds500)

---

## Project Workflow

1. Load the BSDS500 images and ground-truth annotations
2. Process multiple human-generated boundary annotations
3. Resize and normalize the image data
4. Visualize original images and ground-truth boundaries
5. Build a compact U-Net architecture
6. Train the model using training and validation data
7. Monitor training loss and Dice coefficient
8. Evaluate the model on the independent test set
9. Generate boundary predictions
10. Save the trained model

---

## U-Net Architecture

The model uses a compact **encoder-decoder U-Net architecture**.

The encoder extracts visual features from the input images, while the decoder reconstructs spatial information for pixel-level boundary prediction.

**Skip connections** connect encoder and decoder layers to preserve important spatial information.

Main components:

- Convolutional blocks
- Max Pooling
- Bottleneck layer
- Upsampling layers
- Skip connections
- Sigmoid output layer

The model contains approximately **118,000 trainable parameters**.

---

## Model Training

The model was trained using:

- **Optimizer:** Adam
- **Loss Function:** Binary Crossentropy
- **Metric:** Dice Coefficient
- **Maximum Epochs:** 25
- **Batch Size:** 8
- **Early Stopping**
- **ReduceLROnPlateau**

Early Stopping was used to stop unnecessary training epochs, while learning-rate reduction adjusted the learning rate when validation performance stopped improving.

---

## Model Evaluation

The trained U-Net model was evaluated on the independent test dataset.

| Metric | Result |
| --- | ---: |
| Test Loss | **0.0793** |
| Test Dice Score | **0.0586** |

The results indicate that the model learned visible boundary patterns, while the Dice score suggests that further improvement is possible.

---

## Predictions

The model generates pixel-level boundary maps for unseen test images.

Predictions are compared with:

- Original images
- Ground-truth boundaries
- Predicted boundaries

This allows a visual comparison between the human-generated annotations and the boundaries detected by the model.

---

## Technologies

- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- SciPy
- Pillow
- Jupyter Notebook
- Kaggle

---
