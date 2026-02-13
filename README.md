# Brain MRI Tumor Segmentation – Otsu vs Sauvola

This project compares **Global Otsu Thresholding** and **Adaptive Sauvola Thresholding** for brain tumor segmentation on MRI images.

##  Objective

- Segment tumor regions from MRI slices.
- Compare global vs adaptive thresholding.
- Evaluate performance using:
  - Dice Coefficient
  - Jaccard Index (IoU)

---

##  Dataset

**Dataset Used:** Brain Tumor Segmentation Dataset (Kaggle)

- `image/` → MRI slices
- `mask/` → Corresponding binary tumor masks
- Subfolders (0–3) represent tumor categories.

---

##  Methods

### Global Otsu Thresholding
- Computes a single global threshold.
- Separates foreground and background using histogram variance.

### Adaptive Sauvola Thresholding
- Computes threshold locally.
- Adapts to local intensity variations.

---

## Evaluation Metrics

- **Dice Coefficient**
  
  Dice = 2|A ∩ B| / (|A| + |B|)

- **Jaccard Index (IoU)**
  
  IoU = |A ∩ B| / |A ∪ B|

Where:
- A = Ground truth mask
- B = Predicted segmentation

---

##  Results

### Overall Performance (Mean ± Standard Deviation)

| Method   | Dice (Mean ± Std) | Jaccard (Mean ± Std) |
|----------|-------------------|----------------------|
| Otsu     | 0.0609 ± 0.0000   | 0.0314 ± 0.0000      |
| Sauvola  | 0.0344 ± 0.0000   | 0.0175 ± 0.0000      |

---

###  Analysis

- **Otsu** performed slightly better than Sauvola in both Dice and Jaccard scores.
- However, both methods achieved very low segmentation accuracy.
- Global Otsu thresholding tends to segment large high-intensity regions such as the skull and surrounding tissue.
- Sauvola, while adaptive, produces noisy local regions and fails to consistently isolate tumor boundaries.
- The near-zero standard deviation indicates consistent behavior across evaluated samples.

---

###  Key Insight

Simple intensity-based thresholding methods are not suitable for accurate brain tumor segmentation due to:
- Overlapping intensity distributions between tumor and healthy brain tissue.
- Sensitivity to brightness variations and image contrast.
- Lack of spatial and contextual understanding.

Advanced segmentation approaches such as region-based methods or deep learning architectures (e.g., U-Net) are more appropriate for this task.

## Future Work

- Apply skull stripping before segmentation
- Use morphological post-processing
- Explore CNN-based segmentation (e.g., U-Net)
