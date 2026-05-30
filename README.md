# Brain Tumor Image Detection

A deep learning project aimed at accurately classifying MRI images into two categories: **Brain Tumor** and **Healthy** (No Tumour). This repository implements both a baseline model and a proposed hybrid architecture with image preprocessing to achieve state-of-the-art results.

## Overview

Brain tumors are abnormal growths of tissue in the brain or central spinal canal that can disrupt proper brain function. Early and accurate detection is crucial for effective treatment. This project utilizes deep learning, specifically Convolutional Neural Networks (CNNs), to automate the detection process from MRI scans.

### Base Pipeline
The **Base Pipeline** serves as our baseline approach. It utilizes the standard **ResNet-50** architecture, a powerful deep convolutional network that employs residual learning to alleviate the vanishing gradient problem. In this pipeline, the MRI images undergo standard resizing and normalization before being passed into the ResNet-50 model. The model extracts deep features and classifies the images into 'Brain Tumor' or 'Healthy' categories. 

### Proposed Pipeline (ResNet-DenseNet Hybrid + CLAHE)
The **Proposed Pipeline** introduces significant enhancements to improve both feature extraction and diagnostic accuracy:
1.  **Image Preprocessing (CLAHE):** MRI images often suffer from poor contrast, making it difficult to distinguish tumor boundaries. We apply **Contrast Limited Adaptive Histogram Equalization (CLAHE)**, a technique that improves the local contrast and enhances the definitions of edges in each region of the MRI scan.
2.  **Hybrid Architecture:** We designed a custom **ResNet-DenseNet** hybrid model. By combining ResNet's residual connections (which preserve gradient flow) with DenseNet's dense connectivity (which encourages feature reuse and reduces parameter count), the hybrid model captures a richer set of features from the enhanced MRI scans, leading to state-of-the-art classification performance.

## Dataset & Sample Images

The dataset used is the [Brain Tumor Dataset](https://www.kaggle.com/datasets/preetviradiya/brian-tumor-dataset) downloaded from Kaggle (automatically handled within the notebooks using `kagglehub`). It contains images classified into two main classes: **Brain Tumor** and **Healthy**.

Here are some sample MRI images from the dataset:

<p align="center">
  <img src="Brain Tumor Data Set/Brain Tumor Data Set/Brain Tumor/Cancer (1).jpg" alt="Brain Tumor" width="300" style="margin-right: 10px; border-radius: 8px;"/>
  <img src="Brain Tumor Data Set/Brain Tumor Data Set/Healthy/Not Cancer  (1).jpg" alt="Healthy" width="300" style="margin-left: 10px; border-radius: 8px;"/>
</p>
<p align="center">
  <em>Left: MRI scan showing a Brain Tumor. Right: Healthy MRI scan without a tumor.</em>
</p>

## Project Structure

```
Brain-Tumor-Image-Detection/
├── Base Pipeline/
│   ├── Base Code.ipynb       # Baseline implementation using ResNet-50
│   └── ResNet Model/         # Saved baseline models
├── Proposed Pipeline/
│   └── Proposed code.ipynb   # Proposed hybrid model (ResNet-DenseNet) + CLAHE
├── Brain Tumor Data Set/     # Downloaded dataset directory
├── Base Paper.pdf            # Reference research paper
└── README.md
```

## Performance & Results

Both pipelines were evaluated on a dedicated test set. The proposed pipeline shows significant improvements over the baseline.

| Pipeline | Architecture | Preprocessing | Test Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Base Pipeline** | ResNet-50 | Standard Resizing/Normalization | **97.33%** | 97.47% | 95.06% | 97.47% |
| **Proposed Pipeline** | **ResNet-DenseNet Hybrid** | **CLAHE** | **99.33%** | 99.29% | 99.38% | 99.33% |

*The proposed ResNet-DenseNet architecture, combined with CLAHE, effectively reduces false negatives (improves recall to 99.38%), which is critical in medical diagnostics.*

## Technologies Used

*   **Deep Learning Framework:** PyTorch
*   **Computer Vision:** OpenCV (cv2) for CLAHE implementation
*   **Data Manipulation:** Pandas, NumPy
*   **Machine Learning Utilities:** Scikit-learn (Classification reports, metrics)
*   **Visualization:** Matplotlib, Seaborn

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/Brain-Tumor-Image-Detection.git
   cd Brain-Tumor-Image-Detection
   ```

2. **Install Dependencies:**
   Make sure you have Python 3.8+ installed. You can install the required packages using:
   ```bash
   pip install torch torchvision opencv-python pandas numpy scikit-learn matplotlib seaborn kagglehub
   ```

3. **Run the Notebooks:**
   Open the Jupyter notebooks in their respective directories and run the cells. The notebooks are designed to automatically download the dataset if it's not present.
   *   To run the baseline model: `Base Pipeline/Base Code.ipynb`
   *   To run the proposed model: `Proposed Pipeline/Proposed code.ipynb`

## License
This project is licensed under the Apache License 2.0. See the `LICENSE` file for details.