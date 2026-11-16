# Bank Marketing Campaign Prediction

## Project Overview

This project uses a Neural Network to predict whether a bank customer will subscribe to a term deposit, based on marketing campaign data.

The model is implemented in **PyTorch**, and different regularization techniques are evaluated to improve generalization and reduce overfitting.

---

## Dataset

**Source:** [Bank Marketing Dataset – Kaggle](https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset)

The dataset contains information about bank customers, including:

- Demographic attributes
- Financial and personal attributes
- Marketing campaign and contact information
- Previous campaign interactions

### Target Variable: `deposit`

| Value | Meaning |
|-------|---------|
| `1`   | Customer subscribed to a term deposit |
| `0`   | Customer did not subscribe |

### Download Instructions:

1. Download the dataset from the Kaggle link above.
2. Extract the downloaded files.
3. Place "bank.csv" inside the "dataset/" directory.

The notebook also attempts to download the dataset using KaggleHub. If automatic downloading is unavailable, it loads the local CSV file instead.

## Technologies

- Python
- Pandas & NumPy
- Scikit-learn
- PyTorch
- Matplotlib & Seaborn
- KaggleHub

## Project Workflow

1. Data Loading and Exploration
2. Data Preprocessing
3. Categorical Feature Encoding (One-Hot Encoding)
4. Train / Validation / Test Split (60% / 20% / 20%)
5. Feature Scaling (MinMaxScaler)
6. Neural Network Implementation
7. Model Training and Evaluation
8. Regularization Experiments
9. Final Model Selection

## Model Architecture

A fully connected Neural Network was implemented using PyTorch.

- Hidden Layers: 52, 94, and 256 neurons
- Activation Function: ReLU
- Output Activation: Sigmoid
- Loss Function: Binary Cross-Entropy
- Optimizer: Adam
- Early Stopping
- Dropout Regularization

## Regularization Experiments

Five configurations were evaluated:

| Experiment | L1  | L2  | Dropout |
|------------|-----|-----|---------|
| Baseline   | No  | No  | 0.1     |
| L1         | Yes | No  | 0.1     |
| L2         | No  | Yes | 0.1     |
| Dropout    | No  | No  | 0.3     |
| Combined   | Yes | Yes | 0.3     |

**Best Experiment:** Dropout (0.3)

The final configuration was selected based on Validation F1-score.

## Final Model Performance

### Test Set Results:

| Metric    | Score |
|-----------|-------|
| Accuracy  | 0.85  |
| Precision | 0.811 |
| Recall    | 0.882 |
| F1-Score  | 0.845 |
| ROC-AUC   | 0.915 |

### Classification Report:

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| 0     | 0.88      | 0.82   | 0.85     |
| 1     | 0.81      | 0.88   | 0.85     |

### Key Findings:

- Dropout with a rate of 0.3 achieved the best validation performance among the tested configurations.
- The final model achieved an ROC-AUC of 0.915 on the test set.
- The model achieved 0.88 recall for customers who subscribed to a term deposit.
- Early stopping was used to reduce overfitting.

### Important Limitation:

The "duration" feature represents the duration of the last contact with a customer.

Since this information is only available after the contact has taken place, the model is intended for prediction using post-contact information. It should not be interpreted as a pre-campaign customer targeting model.

## Installation

Clone the repository and install the required dependencies:

```bash
git clone https://github.com/Alirezagj1/bank-marketing-classification.git
cd bank-marketing-classification
pip install -r requirements.txt
```

### Running the Project

1. Download and place the dataset in the "dataset/" directory.
2. Install the required dependencies.
3. Open the Jupyter Notebook.
4. Run the cells sequentially.

## Author

**Name:** Alireza Gorji

M.Sc. Student in E-commerce | Machine Learning Enthusiast

- **Project Type:** Machine Learning / Binary Classification
- **Framework:** PyTorch