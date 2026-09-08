# Trustworthy Multiclass Network Intrusion Detection

This repository contains the code, configuration files, preprocessing procedures, trained-model information, evaluation scripts, and supporting materials associated with the research study **“Trustworthy Multiclass Network Intrusion Detection Through Comparative Learning, Counterfactual Explainability, and Monte Carlo Dropout Uncertainty: A CICIDS2017 Study.”**

The project investigates trustworthy multiclass network intrusion detection using the publicly available **CICIDS2017** benchmark dataset. Five machine-learning approaches are comparatively evaluated: **Random Forest, XGBoost, LightGBM, Multilayer Perceptron (MLP), and FT-Transformer**.

Beyond conventional predictive performance, the repository supports three complementary aspects of trustworthy intrusion detection:

1. **Comparative predictive performance**
   Evaluation of multiple machine-learning and deep-learning models using multiclass classification metrics, including accuracy, precision, recall, weighted F1-score, and macro F1-score.

2. **Counterfactual explainability**
   Counterfactual explanations are generated using **DiCE (Diverse Counterfactual Explanations)** and evaluated according to properties such as validity, sparsity, diversity, and generation time.

3. **Predictive uncertainty and calibration**
   **Monte Carlo Dropout** is applied to the FT-Transformer to estimate predictive uncertainty using repeated stochastic forward passes. The analysis includes confidence, predictive entropy, mutual information, variation ratio, calibration, Brier score, expected calibration error, selective prediction, and risk-coverage analysis.

## Dataset

The experiments use the publicly available **CICIDS2017** benchmark dataset developed by the Canadian Institute for Cybersecurity.

The original dataset should be obtained from its official source. The repository does not redistribute the original dataset unless permitted by the dataset's terms of use.

The experimental pipeline processes the network-flow data into a fixed feature representation consisting of **40 numerical features and 14 encoded attack/traffic classes**.

## Main Components

The repository contains implementations and/or supporting files for:

* CICIDS2017 data preprocessing
* Data cleaning
* Feature selection and feature ordering
* Train/test dataset preparation
* Feature scaling
* Label encoding
* Random Forest classification
* XGBoost classification
* LightGBM classification
* Multilayer Perceptron classification
* FT-Transformer classification
* Hyperparameter/configuration settings
* Multiclass performance evaluation
* Class-wise evaluation
* Confusion matrices
* ROC analysis
* DiCE counterfactual explanations
* Counterfactual validity analysis
* Counterfactual sparsity and diversity analysis
* Counterfactual generation-time analysis
* Monte Carlo Dropout uncertainty estimation
* Predictive entropy
* Mutual information
* Variation ratio
* Confidence analysis
* Calibration analysis
* Expected Calibration Error (ECE)
* Multiclass Brier score
* Selective prediction
* Risk-coverage analysis
* Generation of the figures and tables reported in the manuscript

## Reproducibility

The experiments use fixed preprocessing procedures, feature ordering, scaling, model configurations, and random seeds where applicable to facilitate reproducibility.

Users should first obtain the original CICIDS2017 dataset from its official source and then follow the preprocessing and execution instructions provided in this repository.

The exact experimental configuration used in the manuscript is documented in the corresponding configuration/code files.

## Software Environment

The experiments were developed using Python and commonly used machine-learning and scientific-computing libraries, including:

* Python
* TensorFlow / Keras
* scikit-learn
* XGBoost
* LightGBM
* pandas
* NumPy
* SciPy
* Matplotlib
* SHAP, where applicable
* DiCE
* Jupyter Notebook

Exact package versions should be installed according to the provided `requirements.txt` or environment configuration file.

## Repository Structure

```text
Trustworthy-Multiclass-Network-Intrusion-Detection/
│
├── README.md
├── requirements.txt
├── environment.yml
│
├── data/
│   ├── README.md
│   └── processed/
│
├── notebooks/
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_model_training.ipynb
│   ├── 03_model_evaluation.ipynb
│   ├── 04_dice_counterfactuals.ipynb
│   └── 05_mc_dropout_uncertainty.ipynb
│
├── src/
│   ├── preprocessing/
│   ├── models/
│   ├── evaluation/
│   ├── explainability/
│   └── uncertainty/
│
├── configs/
│
├── models/
│
├── results/
│   ├── metrics/
│   ├── counterfactuals/
│   └── uncertainty/
│
├── figures/
│
├── tables/
│
└── LICENSE
```

The exact structure may differ depending on the files included in the final repository.

## Usage

A typical reproduction workflow is:

1. Obtain the CICIDS2017 dataset from its original source.
2. Install the required Python dependencies.
3. Place the dataset files in the directory specified in the data documentation.
4. Run the preprocessing pipeline.
5. Generate the fixed processed dataset and feature representation.
6. Train the baseline and comparative models.
7. Evaluate the models on the held-out test set.
8. Generate DiCE counterfactual explanations.
9. Run the Monte Carlo Dropout uncertainty experiment for the Transformer.
10. Generate the reported metrics, tables, and figures.

## Important Note on Data

The CICIDS2017 dataset is a third-party publicly available benchmark and is not owned by the authors of this repository. Users should obtain the dataset directly from the original provider and comply with its applicable terms of use.

## Research Reproducibility

This repository is intended to provide sufficient implementation details and supporting materials for independent researchers to understand, reproduce, and verify the computational experiments reported in the associated publication.

The repository should be cited when the code or experimental implementation is used in subsequent research.

## Citation

If you use this repository, please cite the associated research article:

> Khan, S. “Trustworthy Multiclass Network Intrusion Detection Through Comparative Learning, Counterfactual Explainability, and Monte Carlo Dropout Uncertainty: A CICIDS2017 Study.”

The final citation should be updated with the journal volume, article number, DOI, and publication year after publication.

## License

The source code in this repository is provided under the license specified in the `LICENSE` file. Third-party datasets and software remain subject to their respective licenses and terms of use.
