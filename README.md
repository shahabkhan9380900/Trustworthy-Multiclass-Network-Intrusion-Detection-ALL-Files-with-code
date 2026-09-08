# Trustworthy Multiclass Network Intrusion Detection

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Scikit--learn](https://img.shields.io/badge/scikit--learn-ML-F7931E.svg)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep%20Learning-FF6F00.svg)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

This repository provides the complete and reproducible implementation of a **trustworthy multiclass Network Intrusion Detection System (NIDS)** developed using the **CICIDS2017 benchmark dataset**.

The project investigates machine-learning and deep-learning approaches for multiclass network intrusion detection while incorporating **model explainability** and **predictive uncertainty estimation**. In addition to conventional classification models, the repository includes a Transformer-based architecture, counterfactual explanations using **DiCE**, and uncertainty estimation using **Monte Carlo Dropout**.

The complete workflow covers:

* Raw network-traffic dataset loading
* Data cleaning and preprocessing
* Feature-matrix construction
* Correlation-based feature selection
* Random Forest-based feature selection
* Label encoding
* Train/test splitting
* Feature standardization
* Classical machine-learning models
* Multilayer Perceptron (MLP)
* Transformer-based intrusion detection
* Counterfactual explainability using DiCE
* Monte Carlo Dropout uncertainty estimation
* Reproducible experimental workflow

---

## Research Objective

Traditional intrusion detection systems often focus primarily on predictive performance. However, high predictive accuracy alone does not necessarily provide sufficient information about **why a model makes a particular security decision or how confident the model is in that decision**.

This project therefore explores a more trustworthy intrusion-detection workflow by combining:

1. **Multiclass intrusion classification**
2. **Feature-selection techniques**
3. **Multiple machine-learning and deep-learning models**
4. **Counterfactual explanations**
5. **Predictive uncertainty estimation**

The objective is to make machine-learning-based intrusion detection more **interpretable, transparent, and reliable** for security analysis.

---

## Dataset

### CICIDS2017

The experiments in this repository use the **CICIDS2017** network intrusion detection benchmark.

CICIDS2017 contains benign network traffic together with multiple realistic attack scenarios and network-flow features suitable for supervised intrusion-detection research.

The dataset is **not included in this repository**.

Users should obtain the dataset from its official source and place the required CSV files in their local working environment before executing the preprocessing notebooks.

> **Important:** Dataset files are not redistributed through this repository.

---

# Methodology

The experimental workflow follows a sequential pipeline.

```text
CICIDS2017 Raw Dataset
        │
        ▼
Data Loading
        │
        ▼
Data Cleaning
        │
        ▼
Feature Matrix Preparation
        │
        ▼
Correlation-Based Feature Selection
        │
        ▼
Random Forest Feature Selection
        │
        ▼
Label Encoding
        │
        ▼
Train/Test Split
        │
        ▼
Feature Standardization
        │
        ├─────────────────────┐
        ▼                     ▼
 Classical ML Models      Deep Learning Models
        │                     │
        │              ┌──────┴──────┐
        │              ▼             ▼
        │             MLP        Transformer
        │
        └──────────────┬──────────────┘
                       ▼
              Multiclass Prediction
                       │
              ┌────────┴────────┐
              ▼                 ▼
      DiCE Explainability   MC Dropout
      Counterfactuals       Uncertainty
```

---

# Repository Structure

The repository currently contains the following main notebooks:

```text
Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code/
│
├── Notebook 1 — Load Raw Dataset.ipynb
│
├── Notebook 2_Data Cleaning.ipynb
│
├── Notebook 3_Feature Matrix Preparation.ipynb
│
├── Notebook 4 – Correlation-Based Feature Selection.ipynb
│
├── Notebook 5 — Random Forest Feature Selection.ipynb
│
├── Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb
│
├── Random forest model code.ipynb
│
├── XGBoost Code.ipynb
│
├── LGBMClassifier Code.ipynb
│
├── MLP code.ipynb
│
├── 6_Build_&_Train_Transformer.ipynb
│
├── DiCE Explainability.ipynb
│
├── Monte Carlo Dropout & Uncertainty Estimation.ipynb
│
└── README.md
```

The repository currently contains **5 commits** and provides the complete notebook-based research workflow.

---

# Experimental Workflow

## 1. Raw Dataset Loading

**Notebook:**

`Notebook 1 — Load Raw Dataset.ipynb`

This notebook is used to load the raw CICIDS2017 network-traffic data and prepare it for subsequent processing.

---

## 2. Data Cleaning

**Notebook:**

`Notebook 2_Data Cleaning.ipynb`

The cleaning stage prepares the network-flow data for machine-learning experiments by handling data-quality issues and preparing the dataset for feature construction.

---

## 3. Feature Matrix Preparation

**Notebook:**

`Notebook 3_Feature Matrix Preparation.ipynb`

This stage constructs the feature matrix used by the classification models.

The resulting feature representation is subsequently used for feature-selection and model-training experiments.

---

## 4. Correlation-Based Feature Selection

**Notebook:**

`Notebook 4 – Correlation-Based Feature Selection.ipynb`

Highly correlated features can introduce redundancy into a machine-learning model.

This notebook performs correlation-based feature analysis to reduce redundant features before subsequent feature-selection steps.

---

## 5. Random Forest Feature Selection

**Notebook:**

`Notebook 5 — Random Forest Feature Selection.ipynb`

Random Forest feature importance is used to identify informative network-traffic features.

This provides a second feature-selection stage following the correlation-based filtering process.

---

## 6. Label Encoding, Train/Test Split and Standardization

**Notebook:**

`Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb`

This stage prepares the final dataset for supervised learning.

The workflow includes:

* Label encoding
* Train/test partitioning
* Feature standardization
* Preparation of the final machine-learning inputs

---

# Machine-Learning Models

The repository implements several classification approaches for multiclass intrusion detection.

## Random Forest

**Notebook:**

`Random forest model code.ipynb`

Random Forest is used as a tree-based ensemble baseline and is also used during feature-selection experiments.

---

## XGBoost

**Notebook:**

`XGBoost Code.ipynb`

XGBoost is implemented as a gradient-boosted decision-tree model for multiclass network intrusion classification.

---

## LightGBM

**Notebook:**

`LGBMClassifier Code.ipynb`

LightGBM provides another gradient-boosting-based approach for evaluating multiclass intrusion detection performance.

---

## Multilayer Perceptron

**Notebook:**

`MLP code.ipynb`

A Multilayer Perceptron neural network is implemented as a deep-learning baseline for network-traffic classification.

---

# Transformer-Based Intrusion Detection

**Notebook:**

`6_Build_&_Train_Transformer.ipynb`

The repository also implements a Transformer-based model for multiclass network intrusion detection.

The notebook contains the model-building and training workflow and is approximately **950 lines / 116 KB** in the current repository.

The Transformer approach is investigated as a deep-learning alternative to conventional tree-based classifiers and MLP models.

---

# Trustworthy AI Components

A key objective of this repository is to move beyond classification accuracy and investigate the **trustworthiness** of model predictions.

## Counterfactual Explainability — DiCE

**Notebook:**

`DiCE Explainability.ipynb`

The repository uses **DiCE (Diverse Counterfactual Explanations)** to generate counterfactual explanations for model predictions.

Counterfactual explanations answer questions such as:

> What would need to change in the observed network-flow features for the model to produce a different prediction?

This provides an interpretable way to investigate individual intrusion-detection decisions.

The current DiCE notebook contains approximately **4,817 lines / 313 KB** of notebook content.

---

# Uncertainty Estimation

**Notebook:**

`Monte Carlo Dropout & Uncertainty Estimation.ipynb`

Monte Carlo Dropout is used to estimate predictive uncertainty.

Instead of considering only the final predicted class, repeated stochastic forward passes can provide information about the stability and uncertainty of model predictions.

This is particularly relevant for cybersecurity applications where uncertain predictions may require additional investigation rather than being treated as fully reliable automated decisions.

---

# Reproducibility

Reproducibility is an important component of this research repository.

The notebooks are organized as a sequential experimental pipeline:

```text
1. Load Raw Dataset
        ↓
2. Data Cleaning
        ↓
3. Feature Matrix Preparation
        ↓
4. Correlation-Based Feature Selection
        ↓
5. Random Forest Feature Selection
        ↓
6. Label Encoding / Train-Test Split / Standardization
        ↓
7. Model Training
        ↓
8. Explainability
        ↓
9. Uncertainty Estimation
```

For reproducible experiments, use the same:

* Dataset version
* Feature-processing procedure
* Train/test configuration
* Label encoding
* Standardization procedure
* Model configuration
* Random seeds where specified in the notebooks

---

# Installation

Clone the repository:

```bash
git clone https://github.com/shahabkhan9380900/Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code.git
```

Enter the repository:

```bash
cd Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code
```

Install the required Python packages:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open the notebooks from the repository and execute them according to the workflow described above.

> **Note:** Dataset paths may need to be adjusted to match the location of the CICIDS2017 files on your computer.

---

# Recommended Execution Order

For reproducing the complete workflow, execute the notebooks in the following order:

### Data Preparation

1. `Notebook 1 — Load Raw Dataset.ipynb`
2. `Notebook 2_Data Cleaning.ipynb`
3. `Notebook 3_Feature Matrix Preparation.ipynb`
4. `Notebook 4 – Correlation-Based Feature Selection.ipynb`
5. `Notebook 5 — Random Forest Feature Selection.ipynb`
6. `Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb`

### Model Development

7. `Random forest model code.ipynb`
8. `XGBoost Code.ipynb`
9. `LGBMClassifier Code.ipynb`
10. `MLP code.ipynb`
11. `6_Build_&_Train_Transformer.ipynb`

### Trustworthiness Analysis

12. `DiCE Explainability.ipynb`
13. `Monte Carlo Dropout & Uncertainty Estimation.ipynb`

---

# Technologies

The project is implemented primarily using the Python scientific-computing and machine-learning ecosystem.

Key technologies include:

* Python
* Jupyter Notebook
* NumPy
* Pandas
* Scikit-learn
* TensorFlow / Keras
* XGBoost
* LightGBM
* DiCE
* Matplotlib
* Seaborn

---

# Research Contributions

The repository brings together several components into a unified trustworthy intrusion-detection workflow:

### Multiclass intrusion detection

Instead of limiting the problem to benign-versus-attack classification, the project investigates multiclass network intrusion detection.

### Feature selection

Two complementary feature-selection approaches are incorporated:

* Correlation-based feature filtering
* Random Forest feature importance

### Model comparison

The repository enables comparison among:

* Random Forest
* XGBoost
* LightGBM
* MLP
* Transformer

### Explainable AI

DiCE is incorporated to generate counterfactual explanations for individual model predictions.

### Uncertainty estimation

Monte Carlo Dropout is used to investigate predictive uncertainty and provide information beyond the predicted class label.

---

# Important Notes

### Dataset availability

The CICIDS2017 dataset is **not included** in this GitHub repository.

Please obtain the dataset from the official Canadian Institute for Cybersecurity source and follow the dataset organization expected by the notebooks.

### Computational requirements

Training deep-learning models and running explainability/uncertainty experiments can require substantially more computational resources than the basic preprocessing notebooks.

For large experiments, sufficient:

* RAM
* CPU/GPU resources
* Disk space

are recommended.

### Notebook paths

The notebooks were developed as a research workflow and may contain local dataset paths. Update those paths before execution if your dataset is stored in a different location.

---

# Citation

If you use this repository, methodology, or implementation in academic research, please cite the associated research work.

```bibtex
@article{shahab2026trustworthy,
  title   = {Trustworthy Multiclass Network Intrusion Detection},
  author  = {Shahab Khan},
  year    = {2026}
}
```

> Replace the citation metadata above with the final published-paper bibliographic information once the associated manuscript has been formally published.

---

# Author

**Shahab Khan**

Department of Cyber Security
Muslim Youth University
Islamabad, Pakistan

Research interests:

* Cybersecurity
* Network Intrusion Detection
* Explainable Artificial Intelligence
* Machine Learning
* Deep Learning
* Transformer Models
* Trustworthy AI
* Zero-Day Attack Detection

---

# License

This project is released under the **MIT License**.

See [`LICENSE`](LICENSE) for details.

---

# Acknowledgements

This work uses the CICIDS2017 benchmark dataset developed by the **Canadian Institute for Cybersecurity**.

The project also builds upon open-source machine-learning, deep-learning, and explainable-AI libraries.

---

## Repository

**GitHub:**
https://github.com/shahabkhan9380900/Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code

If you find this repository useful, consider ⭐ starring the repository and citing the associated research work.
