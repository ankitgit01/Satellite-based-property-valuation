# Satellite-Based Property Valuation using Multimodal Machine Learning

This project builds a **multimodal regression pipeline** to predict property prices by combining **structured tabular data** with **satellite imagery**.  
The goal is to enhance traditional valuation models by incorporating visual context such as surrounding infrastructure, green cover, and neighborhood layout.

---

## Project Overview

Traditional property valuation models rely heavily on numeric and categorical attributes (area, rooms, location codes, etc.).  
This project improves valuation accuracy by integrating **satellite images** extracted using latitude–longitude coordinates, capturing environmental and spatial features that are otherwise ignored.

---
## ▶️ How to Run the Project

- This project is implemented in a **single Jupyter notebook**: complete_source_code.ipynb
- use python 3.12.6 if there is any version mismatch issue.
- Due to GitHub size constraints, raw satellite image folders (`train_images/`, `test2_images/`) are **not included** in the repository.  
- Instead, **precomputed (cached) image features** are provided so the notebook runs end-to-end without errors.

### 1. Clone the repository
### 2. Create and activate virtual environment (Optional)
### 3. Install dependencies : pip install numpy pandas matplotlib seaborn requests pillow torch torchvision scikit-learn xgboost
### 4. Cached image features (default – recommended)
- To ensure smooth execution without downloading large satellite images, the following cached image feature files are already included in artifacts/
- These files contain CNN-extracted embeddings from satellite images and allow the notebook to run completely and efficiently.

- No image download is required for normal execution.

### 5. Run the notebook: Open and run all cells in complete_source_code.ipynb

### 6. (Optional) Re-download satellite images from scratch (if needed for evaluation)
- If the evaluator wishes to verify the image downloading pipeline:

- Obtain a free API key from https://www.maptiler.com

- Replace the API_KEY constant in the notebook with your own key

- Delete the cached artifacts folder:

- Re-run the notebook

⚠️ Note:
Downloading and processing satellite images is very time-consuming and may take a long time depending on API limits and network speed.

### 7. Expected outputs
- Trained regression models

- Price predictions saved as CSV files

- Evaluation plots and metrics

---

## Methodology

- **Tabular Pipeline**
  - Missing value check
  - Duplicate id removal
  - Feature scaling and encoding
  - Feature selection (Dropping the noisy features)
  - Gradient-boosted regression (XGBoost)

- **Image Pipeline**
  - Satellite image acquisition via maptiler.com API key
  - Speeding up image download by parallel download using using two different API keys
  - CNN-based feature extraction (pretrained ResNet-18)
  - Image embeddings converted to numeric vectors (X_image.npy) and saved to avoid repeated computation in subsequent runs

- **Multimodal Fusion**
  - Concatenation of tabular and image features before training -> Early fusion architecture
  - late fusion architecture : separate models were trained for tabular and image features and the final predictions were obtained using a weighted (fine tuned) combination of both model outputs

---

## 📂 Dataset Handling

⚠️ **All the Satellite images are not included in this repository due to size constraints (~1.5 GB). Only 10-12 are uploaded in the folder**

- Images are programmatically downloaded using latitude and longitude
- Each image is saved using the row `id` as filename
- A download script is provided to reproduce the dataset locally

---

## 📊 Model Output

- Evaluation : (Late fusion architecture performed the best)
  - R² Score : 0.908
  - Mean Absolute Error (MAE) : 106296
- Final model trained on full dataset after validation
- Grad-CAM was used to visualize which regions of satellite images most influenced the model’s predictions.

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- PyTorch / Torchvision
- Rasterio
- Maptiler API

---

## 📌 Notes

- This repository focuses on **reproducibility**
- Large datasets (test2_images and train_images folder) are intentionally excluded
- Suitable for academic projects and ML portfolios

---
