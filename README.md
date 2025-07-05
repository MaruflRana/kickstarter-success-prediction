# Kickstarter Success Prediction 🚀

This project leverages machine learning to predict the success or failure of Kickstarter campaigns based on their initial attributes. By analyzing historical campaign data, we aim to identify key factors influencing a project's outcome, providing valuable insights for creators and backers alike.

---

## 📊 Dataset Overview

We use the “400,000 Kickstarter Projects” dataset by toshimelonhead on Kaggle. It contains **≈400 000** records of campaigns launched between 2009 and 2018. Below is a summary of the main columns:

| Column               | Description                                                                                  |
|----------------------|----------------------------------------------------------------------------------------------|
| `id`                 | Numeric identifier for each project                                                          |
| `name`               | Project title                                                                                |
| `category`           | Subcategory (e.g. “Rock”, “Tabletop Games”)                                                  |
| `main_category`      | Broad category (e.g. “Music”, “Games”)                                                       |
| `currency`           | Currency code in which the goal was set (e.g. “USD”, “GBP”)                                  |
| `deadline`           | Date the campaign ended (YYYY‑MM‑DD)                                                         |
| `goal`               | Funding goal (in original currency units)                                                    |
| `launched`           | Launch timestamp (YYYY‑MM‑DD HH:MM:SS)                                                       |
| `pledged`            | Pledged amount (in original currency units)                                                  |
| `state`              | Final status (e.g. “successful”, “failed”, “canceled”, “live”)                              |
| `backers`            | Number of backers                                                                           |
| `country`            | Country code where the campaign was hosted (e.g. “US”, “GB”)                                 |
| `usd_pledged`        | Pledged amount converted to USD using project‐specific exchange rates                        |
| `usd_goal_real`      | Goal amount converted to USD using current exchange rates                                    |
| `usd_pledged_real`   | Pledged amount converted to USD using current exchange rates                                 |

---

## 📈 Key Results & Findings

After a comprehensive analysis and model comparison, the final **Random Forest Classifier** proved to be the most effective model.

- **Final Model Accuracy**: ~78%  
- **Recall (for 'Successful' class)**: ~69%, showing a strong ability to identify successful campaigns  
- **Key Feature Insights**: The model identified the project's **funding goal**, **launch date** (year, day of week), and **category** as the most influential factors in predicting its success

---

## 🔁 Project Workflow

This project follows a standard supervised machine learning pipeline:

1. **Data Loading**  
   - Read `kickstarter.csv` into a pandas DataFrame with exception handling  
   - Inspect `df.head()`, `df.info()`, and missing-value counts  

2. **Exploratory Data Analysis (EDA)**  
   - Plot distributions of `usd_goal_real`, launch dates, and success rates  
   - Compare success across categories and countries  
   - Identify outliers and class imbalances  

3. **Feature Engineering**  
   - Convert `launched` to datetime  
   - Create `day_of_week`, `is_weekend`, and `launch_year` features  
   - Map `state` to binary `binary_state` (1 = successful, 0 = failed)  

4. **Data Cleaning & Preprocessing**  
   - Filter to only `successful` and `failed` campaigns  
   - Drop leaky columns (`usd_pledged`, `backers`, `state`) and other metadata  
   - One-hot encode categorical variables (`category`, `main_category`, `country`)  
   - Split into train/test sets (80/20)  

5. **Model Training**  
   - Train a Random Forest Classifier with `class_weight='balanced'`  
   - Optionally train XGBoost or LightGBM for comparison  

6. **Model Evaluation**  
   - Calculate accuracy, precision, recall, and F1-score  
   - Plot confusion matrix and ROC curve  
   - Compute ROC AUC  

7. **Feature Importance Analysis**  
   - Extract feature importances from the best model  
   - Visualize the top 20 features in a bar chart  

---

## 🛠️ Getting Started

### Prerequisites

- Python 3.7+  
- pip (Python package installer)

### Installation & Setup

```bash
git clone https://github.com/MaruflRana/kickstarter-success-prediction.git
cd kickstarter-success-prediction
pip install -r requirements.txt
