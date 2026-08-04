# EEG-Channel-Reduction
An end-to-end EEG emotion recognition framework that evaluates the impact of channel reduction using five different machine learning and graph neural network pipelines on the DEAP dataset.

# EEG Emotion Recognition through Channel Reduction using Machine Learning and Graph Neural Networks

## Overview

This repository contains my work completed during the **Summer Research Internship Programme (SRIP)** at the **Centre for Neuroinformatics (CNI)**.

The objective of this project is to investigate the effect of **EEG channel reduction** on emotion recognition performance. The study evaluates how reducing the number of EEG electrodes influences classification accuracy while comparing traditional machine learning and graph-based deep learning approaches.

The experiments were conducted using the **DEAP (Database for Emotion Analysis using Physiological Signals)** dataset and include multiple feature extraction techniques, preprocessing pipelines, and classification models.

---

## Objectives

- Validate the integrity of the DEAP dataset before experimentation.
- Reduce EEG channels while preserving classification performance.
- Compare statistical and frequency-domain feature extraction methods.
- Compare Random Forest and Deep Graph Convolutional Neural Network (DGCNN) approaches.
- Evaluate model performance under different channel configurations.
- Compare the proposed approaches with existing methods from the literature.

---

## Dataset

> **Note:** The dataset is not included in this repository due to licensing restrictions.

This project uses the **DEAP (Database for Emotion Analysis using Physiological Signals)** dataset for EEG-based emotion recognition.

The dataset contains EEG recordings collected from participants while watching emotional music videos and includes annotations for:

- Valence
- Arousal
- Dominance
- Liking

The experiments in this repository were conducted using the **Kaggle-hosted version** of the DEAP dataset.

**Kaggle Dataset:**
[https://www.kaggle.com/datasets/fdskjlajlkfdsa/emotion-recognition-eeg-datasets]

**Original DEAP Dataset:**
https://www.eecs.qmul.ac.uk/mmv/datasets/deap/

> **Note:** The dataset is not included in this repository due to licensing restrictions.

---

# Project Workflow

```
DEAP Dataset
      │
      ▼
Dataset Validation
      │
      ▼
Removal of Peripheral EEG Channels
(40 → 32 Channels)
      │
      ▼
Data Preprocessing
      │
      ├────────────────────────────────────┐
      │                                    │
      ▼                                    ▼
Classical ML Pipeline                 DGCNN Pipeline
      │                                    │
      ├──────────────┐               ┌──────┴──────┐
      ▼              ▼               ▼             ▼
Mean-Variance     Band Power     Mean-Variance   Band Power
Features          Features        Features       Features
      │              │               │              │
      ▼              ▼               ▼              ▼
Random Forest   Random Forest   Random Forest  Random Forest
                         │
                         ▼
                     DGCNN Model
                         │
                         ▼
Performance Evaluation
                         │
                         ▼
Model Comparison
                         │
                         ▼
Comparison with Existing Studies
```

---

# Methodology

The project was completed in the following stages:

### 1. Dataset Validation

The DEAP dataset was first validated to ensure the correctness of the downloaded data before beginning model development.

---

### 2. EEG Channel Reduction

The original EEG recordings contain **40 channels**.

The first **8 peripheral channels** were removed since they primarily capture peripheral physiological activity rather than cortical EEG signals, resulting in **32 EEG channels** for further experimentation.

---

### 3. Data Preprocessing

The EEG recordings were preprocessed and transformed into suitable formats for both classical machine learning models and graph neural network models.

---

### 4. Random Forest using Statistical Features

A Random Forest classifier was trained using statistical features extracted from the EEG signals:

- Mean
- Variance

---

### 5. Random Forest using Frequency-Domain Features

A second Random Forest classifier was trained using frequency-domain information by extracting band power features from:

- Delta
- Theta
- Alpha
- Beta
- Gamma

frequency bands.

---

### 6. Dynamic Graph Convolutional Neural Network (DGCNN)

A DGCNN model was implemented to learn spatial relationships between EEG electrodes using graph neural networks.

---

### 7. Random Forest Models using the DGCNN Pipeline

To enable a fair comparison between classical machine learning and graph-based learning, two additional Random Forest models were trained using the same preprocessing pipeline employed by the DGCNN model:

- Random Forest (Mean-Variance Features)
- Random Forest (Band Power Features)

---

### 8. Comparative Analysis

Performance comparisons were carried out across the implemented approaches to analyze the effect of:

- Feature extraction methods
- Model architecture
- Preprocessing pipeline
- Number of EEG channels

---

### 9. Comparison with Existing Studies

The obtained results were compared with selected existing approaches from the literature to evaluate the effectiveness of the proposed methodology.

---

# Models Implemented

| Pipeline | Features | Model |
|----------|----------|-------|
| Pipeline 1 | Mean + Variance | Random Forest |
| Pipeline 2 | Band Power | Random Forest |
| Pipeline 3 | Mean + Variance (DGCNN Pipeline) | Random Forest |
| Pipeline 4 | Band Power (DGCNN Pipeline) | Random Forest |
| Pipeline 5 | Graph Representation of EEG | DGCNN |

---

# Experimental Setup

Each model was evaluated using four different channel configurations:

- 32 Channels
- 16 Channels
- 8 Channels
- 4 Channels

The evaluation was performed separately for:

- Valence
- Arousal
- Dominance
- Liking

using metrics including:

- Accuracy
- Precision
- Recall
- F1-Score
- Balanced Accuracy
- ROC-AUC

---

# Repository Structure

```
EEG-Emotion-Recognition
│
├── notebooks/
├── data/
├── models/
├── results/
├── assets/
├── README.md
├── requirements.txt
└── LICENSE
```

---

# Key Findings

- EEG channel reduction can significantly reduce computational complexity while maintaining competitive performance.
- Different feature extraction techniques perform differently across emotion recognition tasks.
- Classical machine learning and graph neural networks exhibit different strengths depending on the preprocessing pipeline.
- **The optimal number of EEG channels is emotion-dependent rather than universal.**

---

# Technologies Used

- Python
- NumPy
- Pandas
- SciPy
- Scikit-learn
- PyTorch
- TorchEEG
- Matplotlib
- Jupyter Notebook

---

# Future Work

- Subject-independent emotion recognition
- Transformer-based EEG models
- Attention-based Graph Neural Networks
- Real-time EEG emotion recognition
- Edge AI deployment for Brain-Computer Interface applications

---

# Acknowledgements

This work was completed as part of the **Summer Research Internship Programme (SRIP)** at the **Centre for Neuroinformatics (CNI)**.

---

# Author

**Sayantan Sengupta**

B.Tech Computer Science Engineering

VIT Chennai
