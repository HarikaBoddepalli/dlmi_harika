**1.Brain MRI Tumor Segmentation(Global Otsu vs Sauvola Adaptive Thresholding)**

**Project Overview:**

#The objective is to analyze and evaluate:

Global Otsu Thresholding

Sauvola Adaptive Thresholding

#Segmentation performance is evaluated using:

Dice Coefficient

Jaccard Index (IoU)

The goal is to understand the behavior of global vs adaptive thresholding methods in complex medical imaging scenarios.

**Dataset:**

Dataset: Brain Tumor Segmentation Dataset (Kaggle)

Total Images: 4237

Binary tumor masks (0 = background, 1 = tumor)

Multi-class folder structure (0,1,2,3 tumor categories)

Each MRI slice has a corresponding ground truth segmentation mask.

**Results:**
| Method  | Average Dice | Average Jaccard |
| ------- | ------------ | --------------- |
| Otsu    | 0.044        | 0.023           |
| Sauvola | 0.028        | 0.014           |

**Observations:**

Otsu often segments the entire brain region rather than isolating tumor.

Sauvola produces noisy local segmentation due to intensity variation.

Tumor regions occupy a very small portion of the image, leading to low Dice scores.

#Both classical thresholding methods struggle due to:

Intensity overlap between tumor and normal tissue

**Key Learning:**

This experiment demonstrates that:

Global thresholding is insufficient for complex medical segmentation.

Adaptive thresholding improves local sensitivity but still fails in subtle tumor contrast cases.

**Conclusion:**

Global and adaptive thresholding methods were evaluated on 4237 MRI images. Both approaches achieved low Dice scores, indicating that classical intensity-based segmentation techniques are insufficient for accurate tumor delineation in complex brain MRI datasets.



**2.White Blood Cell Segmentation — K-Means vs Fuzzy C-Means**
**Project Overview:**

This project implements and compares Hard Clustering (K-Means) and Soft Clustering (Fuzzy C-Means) for the task of White Blood Cell (WBC) nucleus segmentation.

The objective is to analyze how hard and soft clustering techniques perform in medical image segmentation and evaluate their boundary accuracy using quantitative metrics.

**Assignment Objectives:**

Segment WBC nucleus and cytoplasm from microscopic images.

**Implement:**

K-Means Clustering (Hard Clustering)

Fuzzy C-Means Clustering (Soft Clustering)

**Compare segmentation performance using:**

Dice Coefficient

**Understand differences between:**

Hard vs Soft clustering

Crisp vs probabilistic pixel assignment

**Dataset**

Dataset Name: KRD WBC Dataset
Source: Kaggle
Images: Microscopic blood smear images
Annotations: Binary ground truth masks for nucleus segmentation

**Dataset contains:**

train/images

train/mask

val/images

val/mask

**Methodology:**
**1️.Preprocessing**

Images converted from RGB to LAB color space

For FCM:

Gaussian smoothing applied

Only A and B channels used (better stain separation)

**2️.K-Means (Hard Clustering)**

Number of clusters: 3

Background

Cytoplasm

Nucleus

Each pixel assigned strictly to one cluster.

Best cluster selected based on highest Dice score with ground truth.

**3️.Fuzzy C-Means (Soft Clustering)**

Number of clusters: 3

Fuzziness parameter: m = 1.5

Each pixel assigned membership values across clusters.

Final segmentation obtained using maximum membership.

Best cluster selected using Dice comparison.

**Results (20 Images Evaluation):**
Method	Average Dice Score
K-Means (Hard Clustering)	0.758
Fuzzy C-Means (Soft Clustering)	0.790

**Analysis:**

Fuzzy C-Means achieved higher Dice score.

Soft clustering better handles ambiguous boundary pixels.

Hard clustering performs well but struggles in uncertain regions.

LAB color space improves segmentation quality significantly.

**Key Learning Outcomes:**
**Hard Clustering (K-Means):**

Fast and simple

Crisp boundaries

Sensitive to overlapping intensities

**Soft Clustering (FCM):**

Probabilistic membership

Better boundary handling

More suitable for medical imaging

**Conclusion:**

The experimental results demonstrate that Fuzzy C-Means outperforms K-Means in WBC nucleus segmentation.

Soft clustering provides better boundary accuracy due to its ability to model pixel-level uncertainty, making it more suitable for medical image segmentation tasks.



**3.Retinal Vessel Extraction (Niblack vs Sauvola)**

**Objective:**
Extract thin blood vessels from retinal fundus images.

**Methods:**

Niblack Thresholding

Sauvola Thresholding

**Dataset:**
Kaggle — DRIVE Dataset

**Comparison:**
Sensitivity for thin vessel detection

**Key Findings:**
Adaptive thresholding performs better than global methods.
Sauvola is more stable than Niblack in low-contrast regions, but thin vessel detection remains challenging.

**Learning:**
Understanding local threshold behavior on thin structures.

**4.Cell Nuclei Separation (Watershed)**

**Objective:**
Separate touching or overlapping cell nuclei.

**Method:**
Marker-controlled Watershed Segmentation

**Dataset:**
Kaggle — Data Science Bowl 2018

**Comparison:**
Watershed with markers vs without markers

**Key Findings:**
Standard watershed causes over-segmentation.
Marker-controlled watershed significantly improves nucleus separation.

**Learning:**
Over-segmentation control and importance of marker selection.
