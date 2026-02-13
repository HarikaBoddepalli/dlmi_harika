#Brain MRI Tumor Segmentation(Global Otsu vs Sauvola Adaptive Thresholding)

##Project Overview:

The objective is to analyze and evaluate:

Global Otsu Thresholding

Sauvola Adaptive Thresholding

Segmentation performance is evaluated using:

Dice Coefficient

Jaccard Index (IoU)

The goal is to understand the behavior of global vs adaptive thresholding methods in complex medical imaging scenarios.

#Dataset

Dataset: Brain Tumor Segmentation Dataset (Kaggle)

Total Images: 4237

Binary tumor masks (0 = background, 1 = tumor)

Multi-class folder structure (0,1,2,3 tumor categories)

Each MRI slice has a corresponding ground truth segmentation mask.

#Results
| Method  | Average Dice | Average Jaccard |
| ------- | ------------ | --------------- |
| Otsu    | 0.044        | 0.023           |
| Sauvola | 0.028        | 0.014           |

#Observations

Otsu often segments the entire brain region rather than isolating tumor.

Sauvola produces noisy local segmentation due to intensity variation.

Tumor regions occupy a very small portion of the image, leading to low Dice scores.

Both classical thresholding methods struggle due to:

Intensity overlap between tumor and normal tissue

#Key Learning

This experiment demonstrates that:

Global thresholding is insufficient for complex medical segmentation.

Adaptive thresholding improves local sensitivity but still fails in subtle tumor contrast cases.

#Conclusion

Global and adaptive thresholding methods were evaluated on 4237 MRI images. Both approaches achieved low Dice scores, indicating that classical intensity-based segmentation techniques are insufficient for accurate tumor delineation in complex brain MRI datasets.
