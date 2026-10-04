# social-media-engagement-analytics-ml

# Social Media Engagement Intelligence & Prediction

An end-to-end data analytics and machine learning project that analyzes social media engagement patterns using **Python and SQL** and builds a machine learning model to predict whether a post belongs to the **top 25% of posts by engagement rate**.

## Project Objective

The project aims to answer the following question:

> **Can we predict whether a social media post will have high engagement using information available before its performance is known?**

The project combines:

* Data cleaning and validation
* Exploratory data analysis
* Feature engineering
* MySQL data storage and SQL analytics
* Machine learning classification
* Model evaluation
* Feature importance analysis

## Dataset

The dataset contains **5,000 social media posts** across multiple platforms, content types, categories, sentiments, and influencer tiers.

### Main Features

* `Post_ID`
* `Timestamp`
* `Platform`
* `Content_Type`
* `Category`
* `Likes`
* `Comments`
* `Shares`
* `Views`
* `Saves`
* `Follower_Count`
* `Engagement_Rate`
* `Hour_of_Day`
* `Day_of_Week`
* `Hashtag_Count`
* `Content_Length`
* `Sentiment`
* `Influencer_Tier`
* `Has_Media`
* `Is_Verified`

The dataset contains **no missing values and no duplicate rows**.

## Tools & Technologies

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **MySQL**
* **SQL**
* **Jupyter Notebook**
* **Joblib**

## Project Workflow

```text
Raw Dataset
     ↓
Data Loading
     ↓
Data Understanding
     ↓
Data Cleaning & Validation
     ↓
Feature Engineering
     ↓
Exploratory Data Analysis
     ↓
MySQL Data Storage & ETL
     ↓
SQL Analytics
     ↓
Machine Learning
     ↓
Model Evaluation
     ↓
Feature Importance
     ↓
Final Results
```

## Data Cleaning & Validation

The dataset was checked for:

* Missing values
* Duplicate rows
* Unique post IDs
* Data types
* Categorical value distributions
* Numerical summary statistics
* Extremely high engagement-rate values

The final dataset contains:

* **5,000 rows**
* **21 columns**
* **0 missing values**
* **0 duplicate rows**
* **5,000 unique posts**

## Exploratory Data Analysis

The project analyzes engagement patterns across:

* Social media platforms
* Content types
* Content categories
* High-engagement posts
* Follower count versus engagement rate

### Key Findings

**Platform performance**

TikTok recorded the highest average engagement rate at approximately **41.83**, followed by YouTube at **10.46**.

**Content type performance**

The highest average engagement rates were observed for:

1. Stitch — 45.38
2. Duet — 41.63
3. Video — 20.41

**Category performance**

The highest average engagement categories were:

1. Lifestyle — 19.13
2. Travel — 15.21
3. Technology — 13.96

**High-engagement posts**

TikTok had the highest proportion of high-engagement posts at approximately **74.27%**.

## Feature Engineering

A binary target variable called `High_Engagement` was created.

Posts at or above the **75th percentile of Engagement_Rate** were classified as high engagement.

```text
High_Engagement = 1 → Top 25% of engagement
High_Engagement = 0 → Remaining posts
```

This resulted in:

* **1,250 high-engagement posts**
* **3,750 non-high-engagement posts**

### Machine Learning Features

The model uses information that can be available before post performance is known:

* Platform
* Content Type
* Category
* Follower Count
* Hour of Day
* Day of Week
* Hashtag Count
* Content Length
* Sentiment
* Influencer Tier
* Has Media
* Is Verified

Performance-related variables such as likes, comments, shares, views, saves, and engagement rate were excluded from the predictive features to avoid target leakage.

## Machine Learning

Two classification models were evaluated:

* Logistic Regression
* Random Forest

Categorical variables were converted using **One-Hot Encoding**, while numerical variables were passed through the preprocessing pipeline.

The data was divided into:

* **80% training data**
* **20% testing data**

Stratified splitting was used to preserve the class distribution.

## Model Results

| Model               |  Accuracy |    ROC-AUC |
| ------------------- | --------: | ---------: |
| Logistic Regression |     88.0% |     0.9514 |
| Random Forest       | **88.3%** | **0.9515** |

Random Forest was selected as the final model because it achieved slightly better overall performance.

For the `High_Engagement` class, Random Forest achieved approximately **81% recall**, meaning it correctly identified most of the high-engagement posts in the test set.

Five-fold cross-validation produced a mean ROC-AUC of approximately **0.957**, indicating consistent model performance across validation splits.

## Feature Importance

Random Forest feature importance was used to understand which variables contributed most to the model's predictions.

The most important features included:

* Follower Count
* TikTok platform
* Influencer Tier
* Content Length
* Hashtag Count
* Hour of Day
* Content Type

Feature importance indicates the variables used heavily by the model for prediction; it does **not** imply that those variables directly cause higher engagement.

## SQL Analytics

The cleaned dataset was loaded into **MySQL** and analyzed using SQL.

The project includes SQL analysis using:

* `GROUP BY`
* Aggregate functions
* `WHERE`
* `HAVING`
* `CASE`
* Conditional aggregation
* Subqueries
* Common Table Expressions (CTEs)
* `RANK()`
* `ROW_NUMBER()`
* `LAG()`
* `LEAD()`
* `PARTITION BY`
* Window functions

### Examples of SQL Analysis

The analysis includes:

* Average engagement by platform
* Average engagement by category
* High-engagement percentage by platform
* Content-type performance
* Verified versus non-verified performance
* Top posts by platform
* Top content types within each platform
* Top categories within each platform
* Categories performing above their platform average
* Posts performing above their platform average
* High-engagement percentage by category

### Important SQL Findings

TikTok was the only platform whose average engagement rate was higher than the overall dataset average.

The highest-performing content types included **Stitch, Duet, and Video**.

The SQL analysis also showed that **Travel, Technology, and Sports** had some of the highest proportions of high-engagement posts by category.

## Project Structure

```text
social-media-engagement-analytics-ml/
│
├── Social_Media_Engagement_Analysis.ipynb
├── social_media_engagement_clean.csv
├── social_media_engagement_model.pkl
├── README.md
├── LICENSE
└── social_media_engagement_dataset.csv
```

## How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd social-media-engagement-analytics-ml
```

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn mysql-connector-python joblib
```

### 3. Open the Notebook

Open:

```text
Social_Media_Engagement_Analysis.ipynb
```

using Jupyter Notebook or JupyterLab.

### 4. Configure MySQL

Create a local MySQL connection and update the database connection credentials in the notebook.

The project creates the:

```text
social_media_analysis
```

database and loads the cleaned social media data into MySQL.

## Model Output

The trained Random Forest pipeline is saved as:

```text
social_media_engagement_model.pkl
```

The saved model can be loaded using Joblib for future predictions.

## Dataset Attribution

The dataset used in this project was obtained from Kaggle:

**Social Media Engagement Dataset**

Dataset source:

https://www.kaggle.com/datasets/aviral342/social-media-engagement-dataset

Please refer to the original dataset page for its licensing and usage terms.

## Key Project Takeaways

This project demonstrates an end-to-end workflow involving:

* Python data preparation
* Data quality validation
* Exploratory data analysis
* Feature engineering
* MySQL data loading
* SQL analytics
* Classification modeling
* Model evaluation
* Cross-validation
* Feature importance
* Model persistence

The final Random Forest model achieved **88.3% accuracy** and **0.9515 ROC-AUC** on the test set, with approximately **81% recall for high-engagement posts**.

## Author

**Kirti Gangarde**

M.Sc. Computer Science | Data Analytics & Machine Learning
