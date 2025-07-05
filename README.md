# Kickstarter Success Prediction 🚀

This project leverages machine learning to predict the success or failure of Kickstarter campaigns based on their initial attributes. By analyzing historical campaign data, we aim to identify key factors influencing a project's outcome, providing valuable insights for creators and backers alike.

## 📊 Dataset

The dataset used in this project is sourced from Kaggle's [Kickstarter Projects dataset](https://www.kaggle.com/datasets/kemical/kickstarter-projects), which contains information on over 300,000 Kickstarter campaigns. Key features include:

- `category_name`: The specific category of the project.
- `country`: The country where the campaign was launched.
- `usd_goal`: The funding goal in USD.
- `day_of_week`: The day of the week the campaign launched.
- `is_weekend`: Whether the campaign launched on a weekend.
- `binary_state`: The final outcome (0 for Failed, 1 for Successful).

## 🧪 Project Workflow

The project follows a standard machine learning workflow:

1. **Data Loading**: Import the dataset into a pandas DataFrame.
2. **Data Cleaning & Feature Engineering**:
   - Handle missing values and filter relevant campaign states.
   - Engineer new time-based features like `day_of_week` and `is_weekend`.
3. **Data Preprocessing**:
   - One-hot encode categorical variables.
   - Drop unnecessary or leaky columns.
4. **Model Training**:
   - Split the data into training and testing sets.
   - Train a Random Forest Classifier with `class_weight='balanced'` to address class imbalance.
5. **Model Evaluation**:
   - Assess model performance using accuracy, classification report (precision, recall, F1-score), and ROC AUC.
6. **Feature Importance Analysis**:
   - Visualize the top 20 most important features used in model decisions.

## 📈 Results

The final, improved Random Forest model achieved the following performance on the test set:

- **Accuracy**: ~78%
- **Precision (Successful class)**: ~73%
- **Recall (Successful class)**: ~69%
- **Key Feature Insights**:
  - Campaign **funding goal** (usd_goal) is highly influential.
  - The **category** and **country** of the campaign are also strong predictors.
  - Launch timing features like `day_of_week` and `is_weekend` showed moderate predictive power.

## 🛠️ Getting Started

### Prerequisites

Make sure you have the following installed:

- Python 3.7 or higher  
- pip package manager  
- Jupyter Notebook or JupyterLab

### Installation

Clone the repository:

```bash
git clone https://github.com/MaruflRana/kickstarter-success-prediction.git
cd kickstarter-success-prediction
