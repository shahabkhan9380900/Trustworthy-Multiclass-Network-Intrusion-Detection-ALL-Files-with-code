Trustworthy Multiclass Network Intrusion Detection

Reproducible research for robust network security.

![Jupyter Notebook](https://img.shields.io/badge/Jupyter%20Notebook-F37626?logo=jupyter)

This repository provides a complete pipeline for trustworthy multiclass network intrusion detection. It includes reproducible code, data preprocessing steps, machine learning models, and advanced techniques for counterfactual explainability and uncertainty analysis using Monte Carlo dropout. The project utilizes the CICIDS2017 benchmark dataset for its experiments.

*   End-to-end data preprocessing for network traffic.
*   Implementation of various machine learning models for multiclass intrusion detection.
*   Counterfactual explanations to understand model decisions.
*   Monte Carlo Dropout for quantifying model uncertainty.
*   Reproducible research workflow based on the CICIDS2017 dataset.

```bash
# Clone the repository
git clone https://github.com/shahabkhan9380900/Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code.git
cd Trustworthy-Multiclass-Network-Intrusion-Detection-ALL-Files-with-code

# Install required packages (using pip)
pip install -r requirements.txt
```

```python
# Example of how to run a preprocessing notebook (adjust path as needed)
import subprocess

subprocess.run(["jupyter", "nbconvert", "--to", "notebook", "--execute", "preprocessing/data_preprocessing.ipynb"])

# Example of training a model (refer to specific notebooks for details)
# import pandas as pd
# from sklearn.model_selection import train_test_split
# from your_model_module import YourModel
#
# # Load and preprocess data (assuming data_preprocessing.ipynb has been run)
# data = pd.read_csv("path/to/processed_data.csv")
# X = data.drop("label", axis=1)
# y = data["label"]
# X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
#
# model = YourModel()
# model.fit(X_train, y_train)
# accuracy = model.score(X_test, y_test)
# print(f"Model accuracy: {accuracy}")
```

Configuration details can be found within the individual Jupyter notebooks, specifying parameters for preprocessing, model training, and analysis.

Contributions are welcome! Please refer to the `CONTRIBUTING.md` file for guidelines on how to contribute to this project.

MIT License
