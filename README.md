# Kickstarter Success Prediction 🚀

A machine learning project to predict the success or failure of Kickstarter campaigns. This repository contains a Jupyter Notebook that walks through the entire data science workflow, from data cleaning and feature engineering to model training and evaluation.

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Features](#features)  
- [Dataset](#dataset)  
- [Workflow](#workflow)  
- [Getting Started](#getting-started)  
- [Results & Key Findings](#results--key-findings)  
- [Contributing](#contributing)  
- [License](#license)  
- [Contact](#contact)  

---

## Project Overview

The goal of this project is to build a robust classification model that can accurately predict whether a Kickstarter campaign will be successful or fail based on its initial attributes. By analyzing thousands of past campaigns, we can identify key features that are most influential in determining a project's outcome. This can provide valuable insights for creators planning to launch new campaigns.

---

## Features

- **Data Cleaning:** Handles missing values and filters the dataset for relevant campaign states.  
- **Feature Engineering:** Creates new, insightful features from existing data, such as:  
  - `day_of_week`: Extracts the day of the week a campaign was launched.  
  - `is_weekend`: A boolean flag for campaigns launched on a weekend.  
- **Data Preprocessing:** Uses one-hot encoding to convert categorical features into a machine-readable format.  
- **Model Training:** Implements a `RandomForestClassifier` to predict campaign outcomes.  
- **Class Imbalance Handling:** Uses the `class_weight='balanced'` parameter to address the imbalance between successful and failed campaigns.  
- **Model Evaluation:** Assesses model performance using accuracy and a detailed classification report (precision, recall, F1-score).  
- **Feature Importance Analysis:** Visualizes the top 20 most influential features that the model uses for its predictions.  

---

## Dataset

This project uses the Kickstarter Projects dataset, which contains data on over 200,000 campaigns.

- **Source:** The dataset is widely available and a popular version can be found on Kaggle: [Kickstarter Projects on Kaggle](https://www.kaggle.com/datasets/kemical/kickstarter-projects)  
- **Key Features Used:**  
  - `category_name`: The specific category of the project  
  - `country`: The country where the campaign was launched  
  - `usd_goal`: The funding goal in USD  
  - `day_of_week` (Engineered): The day of the week the campaign launched  
  - `is_weekend` (Engineered): Whether the campaign launched on a weekend  
  - `binary_state` (Target): The final outcome (0 for Failed, 1 for Successful)  

---

## Workflow

The project follows a standard machine learning workflow implemented in the `kickstarter_prediction.ipynb` notebook:

1. **Data Loading:** The `kickstarter.csv` dataset is loaded into a pandas DataFrame.  
2. **Exploratory Data Analysis (EDA) & Cleaning:** The data is explored to understand its structure. The target variable `binary_state` is cleaned to only include 'successful' and 'failed' outcomes and converted to a numeric format.  
3. **Feature Engineering:** New time-based features are created from the `launched_at` column to capture temporal patterns.  
4. **Data Preparation:** Unnecessary and "leaky" columns (like `backers_count` and `usd_pledged`, which are post-launch results) are dropped. Categorical features are one-hot encoded.  
5. **Train-Test Split:** The dataset is split into an 80% training set and a 20% testing set.  
6. **Model Training:** A Random Forest Classifier is trained on the training data.  
7. **Model Evaluation:** The trained model's performance is evaluated on the unseen test data.  
8. **Feature Importance Analysis:** The features that contributed most to the model's predictions are identified and visualized.  

---

## Getting Started

### Prerequisites

- Python 3.7 or higher  
- Pip package manager  
- Jupyter Notebook or JupyterLab  

### Installation

Clone the repository:

```bash
git clone https://github.com/your-username/kickstarter-success-prediction.git
cd kickstarter-success-prediction
