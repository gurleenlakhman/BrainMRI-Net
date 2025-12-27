# BrainMRI-Net
**Early Alzheimer’s detection from structural brain MRI using deep learning**

---

## 🧠 Project Motivation
Alzheimer’s disease is a progressive neurodegenerative disorder where early detection is critical for timely intervention and care planning. Structural brain MRI captures neuroanatomical changes associated with disease progression, making it a key modality for computational analysis.

**BrainMRI-Net** explores how machine learning and deep learning models can leverage structural MRI to distinguish between:
- Cognitively Normal individuals (CN)
- Patients with Mild Cognitive Impairment (MCI)
- Patients with Alzheimer’s Disease (AD)

The project emphasizes **robust experimental design, interpretability, and clinical relevance**, rather than solely optimizing predictive performance.

---

## 🎯 Task Definition
- **Problem Type:** Multiclass classification (3 classes)
- **Classes:** CN (Healthy), MCI, AD
- **Input:** Baseline T1-weighted structural brain MRI (one scan per subject)
- **Output:** Predicted diagnostic category {CN, MCI, AD}
- **Dataset:** OASIS-3 (baseline scans only for v1)

---

## 🏷️ Label Mapping Strategy
Clinical diagnostic labels are mapped to model classes using the following rules:

| Dataset Label | Model Class |
|--------------|-------------|
| CN / Normal | CN |
| EMCI, LMCI | MCI |
| MCI (generic) | MCI |
| AD / AD Dementia | AD |
| Other dementia types | Excluded |
| Unknown / missing diagnosis | Excluded |

This controlled mapping reduces label noise and ensures a clinically interpretable 3-class setup.

---

## 🔬 Experimental Design
- **One scan per subject** (baseline visit only)
- **Subject-level data splitting** to prevent data leakage
- **Train / Validation / Test split:** 70% / 15% / 15%
- **Fixed random seed** for reproducibility

---

## 📊 Evaluation Metrics
Given class imbalance and clinical priorities, performance is evaluated using:

- **Primary Metric:** Macro F1 score
- **Secondary Metrics:**  
  - F1 score per class (CN, MCI, AD)  
  - Confusion matrix  
  - Overall accuracy
- **Clinical Focus Metric:** Recall for MCI

Macro-averaged metrics are emphasized to avoid inflated performance from majority classes.

---

## 🧪 Planned Methodology
1. Dataset exploration and metadata analysis  
2. MRI preprocessing (normalization, resizing, standardization)  
3. Baseline models using clinical features (e.g., age, volumetric proxies)  
4. Convolutional Neural Networks (2D → 3D progression)  
5. Regularization and class imbalance handling  
6. Model interpretability via Grad-CAM  
7. Comparative analysis of attention patterns across CN, MCI, and AD  

---
## 📁 Repository Structure

- **`docs/`** — task specifications and documentation  
- **`data/`** — raw and processed MRI data (excluded from version control)  
- **`notebooks/`** — exploratory analysis and experiments  
- **`src/`** — reusable preprocessing and modeling code  
- **`experiments/`** — experiment-specific configurations and outputs  



## 🚧 Project Status
- [x] Task definition
- [x] Repository setup & git safety
- [x] Documentation (README, task spec)
- [ ] Dataset access & ingestion
- [ ] Preprocessing pipeline
- [ ] Baseline models
- [ ] CNN models
- [ ] Interpretability analysis (Grad-CAM)

---

## ⚠️ Disclaimer
This project is intended for **research and educational purposes only**.  
It is **not** a clinical diagnostic tool and should not be used for medical decision-making.
