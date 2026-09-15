# EEG-Based Classification of Alzheimer's Disease

## Overview
This project investigates whether resting-state EEG features can be used to distinguish individuals with Alzheimer's disease (AD) from cognitively normal (CN) individuals using machine learning.

### Research Question
Can machine learning methods identify neurological differences between Alzheimer's disease and cognitively normal individuals from resting-state EEG recordings?

Analysis focuses on **AD vs. CN classification** using frequency-domain EEG features extracted from preprocessed recordings.

---

## Dataset

**Source:** [OpenNeuro ds004504](https://openneuro.org/datasets/ds004504)

The dataset contains resting-state, eyes-closed EEG recordings from three groups:
- Alzheimer's disease (AD)
- Frontotemporal dementia (FTD)
- Cognitively normal (CN)

The dataset contains **88 participants**:
- 36 Alzheimer's disease
- 23 Frontotemporal dementia
- 29 cognitively normal

For the primary machine learning analysis, participants with Alzheimer's disease and cognitively normal participants were selected, resulting in 65 participants.

---

### 1. Frequency-Domain Feature Extraction

EEG recordings were transformed into the frequency domain using Welch's method to estimate power spectral density (PSD).
Four frequency bands were analyzed:

| Frequency Band | Range |
|---|---:|
| Delta | 1–4 Hz |
| Theta | 4–8 Hz |
| Alpha | 8–13 Hz |
| Beta | 13–30 Hz |

Mean spectral power was calculated for each frequency band across all 19 EEG channels.

**19 channels × 4 frequency bands = 76 EEG features per participant**

A logarithmic transformation was applied to the extracted power values before machine learning.

### 2. Machine Learning

The primary classification task was **Alzheimer's disease vs. cognitively normal**.

Three machine learning approaches were compared:
- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest

### 3. Model Evaluation

Models were evaluated using stratified 5-fold cross-validation.

<img width="990" height="490" alt="stats" src="https://github.com/user-attachments/assets/8c1598c6-ad33-49fd-b4a4-37a6b6e55361" />

A majority-class classifier was also used as a baseline for comparison.

---

## Results

The Random Forest model achieved the highest mean cross-validated ROC-AUC among the evaluated models and was selected for further analysis.

<img width="646" height="463" alt="matrix" src="https://github.com/user-attachments/assets/e288337b-a715-4904-ab5b-971d2c5ab8d2" />

This corresponds to:

- **76.9% overall classification accuracy**
- **75.0% recall for Alzheimer's disease**
- **79.3% specificity for cognitively normal participants**
- **55.4% majority-class baseline accuracy**

The model performed above the majority-class baseline on this dataset.
