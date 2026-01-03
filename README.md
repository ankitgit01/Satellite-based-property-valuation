# Satellite-Based Property Valuation using Multimodal Machine Learning

This project builds a **multimodal regression pipeline** to predict property prices by combining **structured tabular data** with **satellite imagery**.  
The goal is to enhance traditional valuation models by incorporating visual context such as surrounding infrastructure, green cover, and neighborhood layout.

---

## Project Overview

Traditional property valuation models rely heavily on numeric and categorical attributes (area, rooms, location codes, etc.).  
This project improves valuation accuracy by integrating **satellite images** extracted using latitude–longitude coordinates, capturing environmental and spatial features that are otherwise ignored.

---

## Methodology

- **Tabular Pipeline**
  - Missing value imputation
  - Feature scaling and encoding
  - Gradient-boosted regression (XGBoost)

- **Image Pipeline**
  - Satellite image acquisition via map API
  - CNN-based feature extraction
  - Image embeddings converted to numeric vectors

- **Multimodal Fusion**
  - Concatenation of tabular and image features
  - Final regression model trained on fused representation

---

## 📂 Dataset Handling

⚠️ **Satellite images are not included in this repository due to size constraints (~1.5 GB).**

- Images are programmatically downloaded using latitude and longitude
- Each image is saved using the row `id` as filename
- A download script is provided to reproduce the dataset locally


---

## 📊 Model Output

- Evaluated using:
  - R² Score
  - Mean Absolute Error (MAE)
- Final model trained on full dataset after validation

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- PyTorch / Torchvision
- Rasterio
- Satellite Map API

---

## 📌 Notes

- This repository focuses on **reproducibility**
- Large datasets are intentionally excluded
- Suitable for academic projects and ML portfolios

---

## 📬 Author

Developed as part of an applied machine learning project on **multimodal regression for real-world valuation problems**.
