# Tree Segmentation Using SegNet

**Advanced Computer Vision Project**  
**National Institute of Technology (NIT), Raipur, Chhattisgarh**

## Student and Faculty Details

- **Student Name:** Anurag Singh
- **Roll Number:** 23115011
- **Branch:** Computer Science and Engineering (CSE)
- **Year:** Fourth Year
- **Semester:** Seventh Semester
- **Institution:** National Institute of Technology, Raipur
- **Submitted To:** Dr. Bunil Kumar Balabantaray
- **Faculty Designation:** Assistant Professor

---

## 1. Project Overview

This project implements a lightweight SegNet-style deep learning architecture for binary tree segmentation in images.

The objective is to identify tree regions in RGB images and separate them from the background through pixel-wise classification.

The model uses an encoder-decoder architecture to extract image features and generate binary segmentation masks.

## 2. Dataset

The project uses the Tree Segmentation Dataset available at:

https://github.com/gabrieldgf4/tree-segmentation-dataset

The dataset contains RGB tree images and their corresponding binary masks.

### Dataset Distribution

| Dataset | Number of Images |
|---|---:|
| Training | 34 |
| Validation | 7 |
| Testing | 8 |
| **Total** | **49** |

Image-mask pairs were checked for matching filenames and dimensions.

## 3. Data Preprocessing

The following preprocessing steps were performed:

- RGB images were resized to 128 × 128 pixels.
- Masks were resized using nearest-neighbour interpolation.
- RGB pixel values were normalized to the range 0–1.
- Masks were converted into binary values (0 for background and 1 for tree).
- Random horizontal flipping with probability 0.5 was applied to training images.
- Dataset splitting was performed using a fixed random seed of 42.

## 4. Model Architecture

A custom lightweight SegNet-style encoder-decoder architecture was implemented using PyTorch.

### Encoder

The encoder consists of three convolutional stages:

- Stage 1: 3 → 32 → 32 channels
- Stage 2: 32 → 64 → 64 channels
- Stage 3: 64 → 128 → 128 channels

Each stage uses convolution, batch normalization and ReLU activation, followed by 2 × 2 max-pooling.

### Decoder

The decoder consists of three corresponding stages. It uses the stored max-pooling indices through max-unpooling to restore spatial dimensions.

The final convolution produces one output channel containing segmentation logits.

**Note:** This is a custom lightweight SegNet-style implementation, not the complete original SegNet architecture.

## 5. Training Configuration

| Parameter | Value |
|---|---|
| Framework | PyTorch |
| Model | Custom lightweight SegNet-style |
| Input Size | 3 × 128 × 128 |
| Output Size | 1 × 128 × 128 |
| Trainable Parameters | 574,849 |
| Loss Function | BCEWithLogitsLoss |
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Epochs | 15 |
| Batch Size | 2 |
| Execution Device | CPU |

The model with the best validation loss was restored after training.

## 6. Results and Evaluation

The model was evaluated on 8 test images.

| Evaluation Metric | Result |
|---|---:|
| Intersection over Union (IoU) | 75.09% |
| Dice Score | 85.77% |
| Pixel Accuracy | 86.22% |
| Best Validation Loss | 0.4172 |

These metrics indicate the overlap between predicted tree regions and ground-truth segmentation masks.

## 7. Project Files

The repository contains the following files:

```text
23115011-Tree-Segmentation-SegNet/
│
├── ACV_SegNet_Tree_Segm_Proj.ipynb
│
├── README.md
│
├── model/
│   └── SegNet_Tree_Model.pth
│
└── results/
    ├── Evaluation_Results.txt
    └── Training_Loss.txt
```

## 8. How to Run the Project

1. Open the Jupyter Notebook in Google Colab.
2. Run the setup cell to install or import the required libraries and download the dataset.
3. Execute the dataset inspection and preprocessing cells.
4. Run the SegNet architecture definition.
5. Execute the training cell.
6. Run the evaluation and prediction visualization cells.
7. Execute the final cell to save the trained model and evaluation results.

### Required Libraries

- PyTorch
- NumPy
- Pillow
- Matplotlib

Git is also required for downloading the dataset repository.

## 9. Limitations

- The dataset contains only 49 image-mask pairs.
- The validation set contains only 7 images.
- Some predicted boundaries and smaller tree structures differ from the actual masks.
- The model is a lightweight custom implementation rather than the full original SegNet architecture.

## 10. Conclusion

This project demonstrates the application of a lightweight SegNet-style convolutional neural network for binary tree segmentation.

The model achieved an IoU of 75.09%, a Dice score of 85.77%, and pixel accuracy of 86.22% on the test dataset.

Further evaluation using a larger and more diverse dataset would be useful to assess and improve its generalization performance.

---

**Project:** Tree Segmentation Using SegNet  
**Course:** Advanced Computer Vision  
**Institution:** NIT Raipur  
**Student:** Anurag Singh  
**Roll Number:** 23115011  
**Academic Session:** 2026
