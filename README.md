# Trustworthy Multiclass Network Intrusion Detection

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Scikit--learn](https://img.shields.io/badge/scikit--learn-Machine%20Learning-F7931E.svg)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep%20Learning-FF6F00.svg)](https://www.tensorflow.org/)
[![CICIDS2017](https://img.shields.io/badge/Dataset-CICIDS2017-red.svg)](https://www.unb.ca/cic/datasets/ids-2017.html)

## Overview

This repository provides the complete research implementation for **Trustworthy Multiclass Network Intrusion Detection** using the **CICIDS2017** benchmark dataset.

The project develops and evaluates multiple machine-learning and deep-learning models for multiclass network intrusion detection and extends conventional classification with two trustworthy-AI components:

* **Counterfactual explainability using DiCE**
* **Predictive uncertainty estimation using Monte Carlo Dropout**

The repository contains the complete notebook-based workflow, including dataset loading, data cleaning, feature-matrix preparation, feature selection, label encoding, train/test preparation, standardization, model training, explainability, and uncertainty analysis.

---

## Research Objectives

The primary objective is to investigate reliable and interpretable machine-learning approaches for multiclass network intrusion detection.

The project focuses on:

1. Multiclass network intrusion classification
2. Reducing redundant network-flow features
3. Comparing classical ML and deep-learning models
4. Investigating Transformer-based intrusion detection
5. Generating counterfactual explanations
6. Quantifying predictive uncertainty
7. Improving the transparency and trustworthiness of NIDS predictions

---

# Dataset

## CICIDS2017

The experiments use the **CICIDS2017** benchmark dataset developed by the Canadian Institute for Cybersecurity.

The repository does **not** redistribute the original dataset.

The model notebooks use a prepared training/testing split with:

* **Training samples:** 1,948,553
* **Testing samples:** 487,139
* **Input features:** 40
* **Number of classes:** 14

The final model input therefore consists of **40 selected network-traffic features** plus the target label.

---

# Research Pipeline

```text
                    CICIDS2017
                         │
                         ▼
                Raw Dataset Loading
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
             Train/Test Preparation
                         │
                         ▼
                Standardization
                         │
            ┌────────────┴────────────┐
            │                         │
            ▼                         ▼
    Classical ML Models        Deep Learning
            │                         │
     ┌──────┼──────┐             ┌────┴────┐
     │      │      │             │         │
     ▼      ▼      ▼             ▼         ▼
    RF    XGBoost LightGBM      MLP    Transformer
     │      │      │             │         │
     └──────┴──────┴─────────────┴─────────┘
                         │
                         ▼
               Multiclass Prediction
                         │
             ┌───────────┴───────────┐
             │                       │
             ▼                       ▼
       DiCE Explainability     MC Dropout
       Counterfactuals         Uncertainty
```

---

# Repository Structure

```text
Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code/
│
├── Notebook 1 — Load Raw Dataset.ipynb
├── Notebook 2_Data Cleaning.ipynb
├── Notebook 3_Feature Matrix Preparation.ipynb
├── Notebook 4 – Correlation-Based Feature Selection.ipynb
├── Notebook 5 — Random Forest Feature Selection.ipynb
├── Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb
│
├── Random forest model code.ipynb
├── XGBoost Code.ipynb
├── LGBMClassifier Code.ipynb
├── MLP code.ipynb
├── 6_Build_&_Train_Transformer.ipynb
│
├── DiCE Explainability.ipynb
├── Monte Carlo Dropout & Uncertainty Estimation.ipynb
│
└── README.md
```

The GitHub repository currently contains these notebooks on the `main` branch.

---

# Experimental Workflow

## 1. Raw Dataset Loading

**Notebook:**

`Notebook 1 — Load Raw Dataset.ipynb`

Loads the CICIDS2017 network-traffic data and prepares the raw data for subsequent processing.

---

## 2. Data Cleaning

**Notebook:**

`Notebook 2_Data Cleaning.ipynb`

Performs data-cleaning operations required before constructing the final machine-learning dataset.

---

## 3. Feature Matrix Preparation

**Notebook:**

`Notebook 3_Feature Matrix Preparation.ipynb`

Constructs the feature matrix and target representation used by the downstream experiments.

---

## 4. Correlation-Based Feature Selection

**Notebook:**

`Notebook 4 – Correlation-Based Feature Selection.ipynb`

Correlation analysis is used to identify redundant or highly correlated features.

This reduces unnecessary feature duplication before the subsequent feature-selection stage.

---

## 5. Random Forest Feature Selection

**Notebook:**

`Notebook 5 — Random Forest Feature Selection.ipynb`

Random Forest feature importance is used to identify informative network-traffic features.

The final experimental models use **40 input features**.

---

## 6. Label Encoding, Train/Test Split and Standardization

**Notebook:**

`Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb`

This stage prepares the final learning data through:

* Label encoding
* Train/test preparation
* Feature standardization
* Final feature matrix construction

The model notebooks use 1,948,553 training samples and 487,139 testing samples with 40 input features.

---

# Machine-Learning Models

The repository evaluates four primary non-Transformer models:

* Random Forest
* XGBoost
* LightGBM
* Multilayer Perceptron (MLP)

---

# Results

The following results are taken directly from the **saved notebook outputs in this repository**.

All four metrics below use the weighted multiclass evaluation reported by the respective notebooks.

| Model             |     Accuracy |    Precision |       Recall |     F1-Score |
| ----------------- | -----------: | -----------: | -----------: | -----------: |
| **XGBoost**       | **99.9062%** | **99.9238%** | **99.9062%** | **99.9124%** |
| **LightGBM**      | **99.8828%** | **99.9089%** | **99.8828%** | **99.8925%** |
| **Random Forest** | **99.7847%** | **99.8828%** | **99.7847%** | **99.8204%** |
| **MLP**           | **85.0850%** | **94.8675%** | **85.0850%** | **88.5943%** |

### XGBoost

XGBoost achieved:

* Accuracy: **0.9990619**
* Precision: **0.9992378**
* Recall: **0.9990619**
* F1-score: **0.9991244**

The classification report also reports a **macro F1-score of 0.9453**, demonstrating that the weighted metrics are substantially higher than the macro metrics because of class imbalance.

### LightGBM

LightGBM achieved:

* Accuracy: **0.9988278**
* Precision: **0.9990889**
* Recall: **0.9988278**
* F1-score: **0.9989247**

The notebook reports a macro F1-score of **0.9271**.

### Random Forest

Random Forest achieved:

* Accuracy: **0.9978466**
* Precision: **0.9988278**
* Recall: **0.9978466**
* F1-score: **0.9982037**

The classification report reports a macro F1-score of **0.8600**.

### MLP

The MLP achieved:

* Accuracy: **0.8508496**
* Precision: **0.9486751**
* Recall: **0.8508496**
* F1-score: **0.8859432**

The class-level results show substantially more variation across the 14 classes than the tree-based models.

---

# Transformer-Based Intrusion Detection

**Notebook:**

`6_Build_&_Train_Transformer.ipynb`

A Transformer-based deep-learning architecture is also implemented for multiclass intrusion detection.

The notebook trains the model with early stopping and learning-rate reduction.

The saved evaluation output reports:

| Metric               |       Result |
| -------------------- | -----------: |
| Evaluation Accuracy  | **99.3346%** |
| Evaluation Precision | **99.4182%** |
| Evaluation Recall    | **99.2202%** |
| Evaluation Loss      | **0.002138** |

The best training epoch was reported as epoch 19, after which early stopping restored the best model weights.

> **Important:** These values are reported as the notebook's evaluation/validation results. They should not be described as an independent held-out test result unless the experimental protocol explicitly establishes that dataset as the final test set.

---

# Model Comparison

Based on the saved weighted metrics:

```text
XGBoost       ████████████████████  99.91% F1
LightGBM      ████████████████████  99.89% F1
Random Forest ████████████████████  99.82% F1
Transformer   ████████████████████  99.42% Precision*
MLP           █████████████████     88.59% F1

* Transformer value is the notebook's evaluation result,
  not labelled here as an independent test-set F1.
```

Among the classical models, **XGBoost provides the highest weighted accuracy and F1-score in the currently saved notebook outputs**.

---

# Why Macro Metrics Matter

Although the weighted scores are extremely high for the tree-based models, the macro scores are lower.

For example:

* XGBoost macro F1: **0.9453**
* LightGBM macro F1: **0.9271**
* Random Forest macro F1: **0.8600**

This difference is important in cybersecurity because a model can achieve very high overall accuracy while performing less effectively on rare attack classes.

Therefore, this repository reports both aggregate performance and class-level classification results rather than relying exclusively on accuracy.

---

# ROC Analysis

The Random Forest and XGBoost notebooks also generate **per-class ROC curves** using the predicted class probabilities.

The ROC analysis is implemented separately for the multiclass classes and visualizes the class-specific false-positive and true-positive rates.

---

# Explainable AI — DiCE

**Notebook:**

`DiCE Explainability.ipynb`

The repository includes a dedicated implementation for **counterfactual explainability using DiCE**.

Counterfactual explanations investigate how changing input network-flow features could alter the model's prediction.

Conceptually:

```text
Original Network Flow
          │
          ▼
     Model Prediction
          │
          ▼
   Counterfactual Search
          │
          ▼
Alternative Feature Configuration
          │
          ▼
     Changed Prediction
```

This provides an additional layer of interpretability beyond simply reporting the predicted attack class.

The DiCE notebook is a substantial implementation containing approximately **4,817 lines** of notebook content.

---

# Predictive Uncertainty — Monte Carlo Dropout

**Notebook:**

`Monte Carlo Dropout & Uncertainty Estimation.ipynb`

The repository also includes a dedicated Monte Carlo Dropout workflow for uncertainty analysis.

The notebook contains approximately **4,153 lines** of content and approximately **1.07 MB** in the current repository.

Monte Carlo Dropout performs multiple stochastic predictions and can be used to estimate the uncertainty associated with model predictions.

```text
Input Network Flow
        │
        ▼
 Multiple Stochastic
    Forward Passes
        │
        ▼
 Probability Estimates
        │
        ▼
 Prediction + Uncertainty
```

This is particularly relevant to cybersecurity because low-confidence predictions can potentially be flagged for further investigation rather than treated as equally reliable automated decisions.

---

# Reproducibility

The experiments use fixed random seeds in the model notebooks.

For example, the Random Forest implementation explicitly sets:

```python
SEED = 42

random.seed(SEED)
np.random.seed(SEED)

os.environ["PYTHONHASHSEED"] = str(SEED)
```

The LightGBM implementation similarly fixes the random seed to **42**.

The repository therefore aims to provide a reproducible notebook-based research workflow.

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

Install the Python libraries used by the notebooks according to the import statements and environment requirements specified within the individual notebooks.

Launch Jupyter:

```bash
jupyter notebook
```

> **Note:** The current GitHub repository does not contain a `requirements.txt` file. Therefore, this README intentionally does not provide a `pip install -r requirements.txt` command.

---

# Recommended Execution Order

## Data Preparation

1. `Notebook 1 — Load Raw Dataset.ipynb`
2. `Notebook 2_Data Cleaning.ipynb`
3. `Notebook 3_Feature Matrix Preparation.ipynb`
4. `Notebook 4 – Correlation-Based Feature Selection.ipynb`
5. `Notebook 5 — Random Forest Feature Selection.ipynb`
6. `Notebook 6 — Label Encoding, TrainTest Split & Standardization.ipynb`

## Model Training

7. `Random forest model code.ipynb`
8. `XGBoost Code.ipynb`
9. `LGBMClassifier Code.ipynb`
10. `MLP code.ipynb`
11. `6_Build_&_Train_Transformer.ipynb`

## Trustworthy AI Analysis

12. `DiCE Explainability.ipynb`
13. `Monte Carlo Dropout & Uncertainty Estimation.ipynb`

---

# Technologies

The project uses the following technologies and libraries:

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

# Key Contributions

This repository provides an integrated experimental workflow combining:

### Multiclass NIDS

Fourteen-class network intrusion classification using CICIDS2017.

### Feature Selection

A two-stage feature-selection workflow involving:

* Correlation-based feature filtering
* Random Forest feature importance

### Model Comparison

Evaluation of:

* Random Forest
* XGBoost
* LightGBM
* MLP
* Transformer

### Explainability

Counterfactual explanations using DiCE.

### Uncertainty

Monte Carlo Dropout-based predictive uncertainty analysis.

### Reproducibility

Fixed random seeds and an ordered notebook workflow.

---

# Important Dataset Note

The CICIDS2017 dataset is not distributed with this repository.

Users should obtain the dataset from the official Canadian Institute for Cybersecurity source and configure the local paths expected by the notebooks.

The current model notebooks reference prepared files such as:

```text
../datasets/CICIDS2017/train_test/CICIDS2017_Train_80.csv
../datasets/CICIDS2017/train_test/CICIDS2017_Test_20.csv
```

These dataset files are not stored in the GitHub repository.

---

# Citation

If you use this repository or its implementation in academic research, please cite the associated research work.

```bibtex
@article{shahab2026trustworthy,
  title   = {Trustworthy Multiclass Network Intrusion Detection},
  author  = {Khan, Shahab},
  year    = {2026}
}
```

> Update the BibTeX entry with the final journal, volume, issue, pages, DOI, and publisher information after publication.

---

# Author

**Shahab Khan**

Department of Cyber Security
Muslim Youth University
Islamabad, Pakistan

### Research Interests

* Cybersecurity
* Network Intrusion Detection
* Explainable Artificial Intelligence
* Trustworthy AI
* Machine Learning
* Deep Learning
* Transformer Models
* Cyber Attack Detection
* Predictive Uncertainty

---

# License

This project is released under the **MIT License**.

---

# Repository

**GitHub:**
https://github.com/shahabkhan9380900/Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code

If you find this repository useful, please consider giving it a ⭐ and citing the associated research work.
