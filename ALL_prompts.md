### prompt 0 (setup)
Context: 
using the well-known dataset from Kaggle https://www.kaggle.com/datasets/blastchar/telco-customer-churn/data;
Predict behavior to retain customers. You can analyze all relevant customer data and develop focused customer retention programs.

Content: 
Each row represents a customer, each column contains customer’s attributes described on the column Metadata.

The data set includes information about:
Customers who left within the last month – the column is called Churn
Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
Demographic info about customers – gender, age range, and if they have partners and dependents

Inspiration
To explore this type of models and learn more about the subject.

Task:
1. Using CTDOC prompts, we are going to clean, analyse, build Machines for forecasting, and visualize the data 
---
### prompt 1
For the uploaded Data, as a Senior Data analyst and Churn specialist working in a telecom company.

Task:
Load the Dataset (which is in a folder called TelcoDataSet from the notebook file)
import libraries.
Run EDA
Identify and address missing values or data
Display basic information
Show a summary statistics

output:
Formatted for Jupyter notebook. Clean executable Python code
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.

using:

Python 3.14.4
Pandas 3.0.2
matplotlib 3.10.8
seaborn 0.13.2
scikit-learn 1.8.0
imbalanced-learn 0.14.1

CONSTRAINTS:
this going to be the only time you should import any library or load the dataset
We are going to use the same dataset every time, so any update/edit is cumulative.

---
### prompt 2
For the uploaded Data, as a Senior Data analyst and Churn specialist working in a telecom company.

Task: 
1. Make a full EDA
2. Detect the DataFrame issues (anomalies, outliers, duplicates, wrong datatype, e.t.c.)
3. Convert categorical columns into appropriate formats for modeling (e.g., encoding).
4. fix datatypes, Standardized Categorical Value

output: 
Formatted for Jupyter notebook. Clean executable Python code
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.
using:
  Python 3.14.4
  Pandas 3.0.2
  matplotlib 3.10.8
  seaborn 0.13.2
  scikit-learn 1.8.0
  imbalanced-learn 0.14.1

CONSTRAINTS:
don't reimport libraries 
don't relaod dataset 
---
### prompt 3
For the used DataFrame, as a Senior visualizetion and Churn specialist well known with best designs 


Task: 
Visualize churn rates across demographics (gender, senior citizen, partner, dependents).
Analyze churn in relation to services (InternetService, TechSupport, OnlineSecurity).
Use bar charts and boxplots to study churn vs. tenure, monthly charges, and contract type.
Identify top 5 variables you believe most influence customer churn.

output: 
Formatted for Jupyter notebook. Clean executable Python code
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.
Deliverables
Visuals (plots, tables) with short captions or explanations.
using:
  Python 3.14.4
  Pandas 3.0.2
  matplotlib 3.10.8
  seaborn 0.13.2
  scikit-learn 1.8.0
  imbalanced-learn 0.14.1

CONSTRAINTS:
don't reimport libraries 
don't relaod dataset 
---
### prompt 4
For the used DataFrame, as a Senior Data analyst and ML, familiar with telecom buisness 

Task: 
Summary 3 key insights with potential business impact.
Identify the top 3 most important features and apply suitable feature engineering techniques based on business needs and model performance.

output: 
Formatted for Jupyter notebook. Clean executable Python code
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.

CONSTRAINTS:
don't reimport libraries
don't relaod dataset
---
### prompt 5
For the used DataFrame, as a Senior Data Science and ML

Task: 
Split the dataset into stratified training and testing sets (80-20) while preserving target class distribution and preventing data leakage.
Train two models (e.g., Logistic Regression, Random Forest, or XGBoost).
Compare model performance using accuracy, recall, precision, and F1-score.
Apply hyperparameter tuning where appropriate and compare performance using cross-validation.
Present feature importance rankings and interpret them in business terms.

output: 
Formatted for Jupyter notebook with model training, evaluation, and explanation. Clean executable Python code
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.
ROC curve and confusion matrix visualizations.
Short report which model you'd recommend and why.
using:
  scikit-learn 1.8.0
  imbalanced-learn 0.14.1

CONSTRAINTS:
don't reimport libraries
don't relaod dataset
---
### prompt 6
For the uploaded Data, as a Senior Data SCience and ML focused on churn analysis and business impact.

Task:
Calculate the average revenue loss per churned customer.
Estimate total expected revenue loss from predicted churners.
Simulate customer retention under two strategies (e.g., discount offer vs. loyalty perks) For each strategy:
  Assume a retention success rate (state assumption clearly)
  Estimate number of customers retained
  Calculate cost of intervention
  Compare against revenue saved
Estimate how many customers you'd need to retain to break even.
Compare which strategy is more cost-effective under different churn scenarios.
Propose a segmentation strategy (e.g., high-risk + high-value customers).
Define segments such as:
  High-risk / high-value
  High-risk / low-value
  Low-risk / high-value
  Low-risk / Low-value
Recommend prioritization strategy for targeting

output:
Formatted for Jupyter notebook. Clean executable Python code.
uses a clean structure and comments
A markdown section explaining any assumptions or decisions made.
Business interpretation of churn cost and retention ROI
Final recommendation of the best retention strategy
A concise 1-page executive memo summarizing:
  key findings
  recommended strategy
  expected business impact

CONSTRAINTS:
don't reimport libraries
don't relaod dataset
---
### prompt 7
For the same DataFrame, as a Senior Data Scientist & Business Analyst in a telecom company 

Task:
1. Visual-Driven Insights
2. Translate each visual insight into clear business meaning.
3. Focus on explaining why this is happening in real-world terms.
4. For each insight, provide at least one direct business action
5. Keep actions realistic and aligned with churn reduction strategies

output:
Formatted for Jupyter notebook. Clean executable Python code.
uses a clean structure and comments
No heavy technical jargon
Focus on clarity and business value
Each insight must lead to an action
Output must be presentation-ready
Structured list of insights
Business-friendly explanations
Actionable recommendations
Prioritized strategy roadmap
A markdown section explaining any assumptions or decisions made.

CONSTRAINTS:
don't reimport libraries
don't relaod dataset
