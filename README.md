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

Folder structure:
Brain Tumor Segmentation Dataset/
│
├── image/
│ ├── 0/
│ ├── 1/
│ ├── 2/
│ └── 3/
│
└── mask/
├── 0/
├── 1/
├── 2/
└── 3/

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

## Observations

- Otsu over-segments high-intensity regions (entire head).
- Sauvola produces noisy local segmentation.
- Both methods fail to isolate tumor accurately.
- Thresholding alone is not sufficient for medical image segmentation.

---

## Conclusion

Simple intensity-based thresholding methods are inadequate for accurate tumor segmentation in MRI images. More advanced techniques such as region-based methods or deep learning models are recommended for reliable performance.

---

## Future Work

- Apply skull stripping before segmentation
- Use morphological post-processing
- Explore CNN-based segmentation (e.g., U-Net)
