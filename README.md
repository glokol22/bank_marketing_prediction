# Bank Marketing Prediction

## Overview

The goal of this project is to predict whether a client will subscribe to a term deposit based on their interactions with the bank. This is a classification problem using the **UCI Bank Marketing Dataset**, and it involves preprocessing the data, handling class imbalances, and evaluating several machine learning models.

---

## Table of Contents

- [Project Description](#project-description)
- [Setup Instructions](#setup-instructions)
- [Data Preprocessing](#data-preprocessing)
- [Handling Class Imbalance](#handling-class-imbalance)
- [Machine Learning Models](#machine-learning-models)
- [Results](#results)
- [License](#license)

---

## Project Description

This project uses the **UCI Bank Marketing Dataset** to predict customer subscriptions to term deposits. It includes several features such as client data, marketing campaign details, and historical information.

The dataset is preprocessed for better model performance and addresses issues such as:
- **Skewed numerical columns**
- **Handling missing or incorrect values**
- **Feature transformations**

---

## Setup Instructions

To get started with the project, follow these steps:

### Clone the Repository

```bash
git clone https://github.com/yourusername/bank-marketing-analysis.git
cd bank-marketing-analysis
```


## Install Dependencies
```bash
pip install -r requirements.txt
```

## Download the Dataset
The dataset can be downloaded directly from the UCI repository or accessed via ucimlrepo:


```python
from ucimlrepo import fetch_ucirepo
dataset = fetch_ucirepo(id=146)
```

## Data Preprocessing

### Renaming Columns 
Ensured all column are properly named( e.g., renaming day_of_week to day).

### Null values 
No significant missing data found, but minor corrections were applied to columns like pdays (converted negative values to zero).

### Categorical Encoding
Applied one-hot encoding to categorical features such as job, marital, and education.

### Feature Scaling
Scaled numerical columns using StandardScaler.

## Handling Class Imbalance
The target variable, y, is imbalanced, with more "no" values than "yes". To address this:

## Resampling Techniques
Applied below sampling techniques to balance the classes.

- 🔄 **SMOTE**
- 🔁 **Random OverSampling**
- 💡 **ADASYN**
- 🟢 **Borderline SMOTE**
- ⚙️ **SVM SMOTE**

## Evaluation Metrics
Used metrics such as Precision, Recall, F1-Score, and ROC-AUC to evaluate models due to the class imbalance.

## Machine Learning Models
Tested various machine learning models to predict client subscriptions:

- ✨ **Logistic Regression**
- 🌳 **Decision Tree Classifier**
- 🌲 **Random Forest Classifier**
- 🧑‍💻 **Support Vector Machine (SVM)**
- 🚀 **Gradient Boosting Classifier**

## Model Evaluation

After analyzing various techniques and their impact on class imbalance, outliers, and model performance, the **XGBoost with SMOTE** model emerges as the optimal choice for the following key reasons:

- **Superior Accuracy and Balance**:  
  **XGBoost with SMOTE** slightly outperforms other methods in terms of accuracy, achieving a score of **0.9025** compared to **0.9015** from Borderline SMOTE. While the difference is minimal, **SMOTE**'s consistent performance across both classes (with good recall for the majority class and acceptable performance for the minority class) ensures reliable results across the board.

- **Effective Handling of Class Imbalance**:  
  SMOTE has proven to be highly effective in generating synthetic data points for the minority class, improving recall for the minority class without significantly compromising the performance on the majority class. This leads to a well-balanced model that mitigates the impact of class imbalance, a critical challenge for our dataset.

- **Better Overall Precision and Recall**:  
  While **Borderline SMOTE** performs slightly better in recall for the minority class, **XGBoost with SMOTE** maintains higher precision for both classes, ensuring fewer false positives and a more stable model for deployment in real-world scenarios.

In conclusion, **XGBoost with SMOTE** strikes the best balance between accuracy, handling of class imbalance, and model stability, making it the most reliable choice for this classification problem. It effectively addresses the challenges posed by outliers and the skewed distribution of the target variable, providing a robust solution for our bank marketing campaign prediction model.


## License
This project is licensed under the MIT License - see the LICENSE file for details.