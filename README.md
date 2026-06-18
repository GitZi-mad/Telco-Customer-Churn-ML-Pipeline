# 📉 Telco Customer Churn — End-to-End ML Pipeline

> **Final Capstone Project** · Global Knowledge × Orange Egypt — AI Advanced Data Analyst Track

A complete, production-style machine learning pipeline built on the IBM Telco Customer Churn dataset. The project covers every stage of a real data science workflow — from raw data ingestion to an executive-ready retention strategy — across **8 structured phases**.

---

## 📌 Project Overview

Customer churn is one of the most expensive problems a telecom company faces. Acquiring a new customer costs 5–7× more than retaining an existing one. This project builds a predictive ML system that identifies at-risk customers **before** they leave, and translates model predictions into **quantified financial impact and actionable retention strategies**.

**Dataset:** IBM Telco Customer Churn (`WA_Fn-UseC_-Telco-Customer-Churn.csv`)  
**Records:** 7,043 customers · 20 features  
**Target:** Binary churn prediction (`Churn`: Yes / No)

---

## 🗂️ Repository Structure

```
Telco-Customer-Churn-ML-Pipeline/
│
├── WA_Fn-UseC_-Telco-Customer-Churn.csv        # Raw dataset
├── Telco_Churn_Engineered_Ready.csv             # Feature-engineered dataset (Phase 4 output)
├── Final_Project.ipynb                          # Full pipeline notebook (Phases 1–8)
├── Telco_Churn_Executive_Presentation.pptx      # Business-facing slide deck
└── README.md
```

---

## 🔬 Pipeline Phases

### Phase 1 — Data Loading & Cleaning
- Identified `TotalCharges` loaded as `object` due to 11 blank-space entries
- Applied domain-informed imputation: 11 affected rows all had `tenure = 0` (new customers with no billing cycle yet), so values were filled with `0.0`
- Moved `customerID` to the DataFrame index to prevent accidental feature leakage

### Phase 2 — EDA & Data Transformation
- Detected and dropped 22 duplicate rows (feature-space duplicates after indexing)
- Standardized `"No internet service"` / `"No phone service"` values to `"No"` to reduce dimensionality
- Applied **Binary Encoding** (0/1) to two-class categorical columns
- Applied **One-Hot Encoding** (`drop_first=True`) to nominal multi-class columns: `InternetService`, `Contract`, `PaymentMethod`
- Generated 4-panel EDA dashboard: class imbalance, numerical distributions, boxplots, correlation heatmap

### Phase 3 — Advanced EDA & Churn Driver Analysis
- Dynamically reverse-mapped encoded values back to readable labels for business-facing visualizations (underlying ML DataFrame untouched)
- Reconstructed OHE-split columns (e.g., `Contract`, `InternetService`) into cohesive categories for bar chart analysis
- Ranked top churn predictors using **absolute Pearson correlation coefficient**

**Key findings:**
| Driver | Insight |
|--------|---------|
| `Contract_Month-to-month` | ~42% churn rate vs. ~3% for 2-year contracts |
| `InternetService_Fiber optic` | Counter-intuitively higher churn than DSL — likely an operational/infrastructure issue |
| `TechSupport` & `OnlineSecurity` | Strong retention anchors — customers who adopt them show robust loyalty |
| `tenure` | Nearly 48% of churners leave within their first 12 months |
| `SeniorCitizen` | Noticeably elevated churn rate; `gender` has near-zero influence |

### Phase 4 — Business Insights & Feature Engineering
Three new features engineered from the strongest churn drivers:

| Feature | Logic | Business Rationale |
|---------|-------|--------------------|
| `Is_New_Customer` | `tenure <= 12` → binary flag | Churn risk is non-linear; the first year is a critical high-risk window |
| `Total_Extra_Services` | Sum of all add-on service columns | Measures customer ecosystem entrenchment / engagement depth |
| `Charge_Spike_Ratio` | `MonthlyCharges / (TotalCharges / tenure)` | Detects promotional period endings and sudden bill shocks |

Dataset expanded from **23 → 26 columns** post-engineering.

### Phase 5 — Predictive Modeling & Hyperparameter Tuning
- **Train/Test Split:** 80/20 with `stratify=y` to preserve the 73%/27% class distribution
- **Scaling:** `StandardScaler` fitted on training set only; test set transformed (never fitted)
- **Class Imbalance:** Addressed with **SMOTE** (Synthetic Minority Over-sampling Technique) applied exclusively on the training set
- **Models trained:**
  - Logistic Regression (interpretable linear baseline)
  - Random Forest (ensemble, handles non-linear interactions)
- **Tuning:** `GridSearchCV` optimized for **F1-Score** and **Recall** on the minority class (Churn = 1)

### Phase 6 — Model Recommendation & Business Report
Both models achieved AUC ≈ 0.84. **Random Forest was selected for deployment** due to its superior balance of Precision and Recall — producing fewer False Positives, which means retention budget is spent efficiently rather than offering discounts to customers who were going to stay anyway.

**Top model-identified churn predictors:**
1. `Contract_Two year` & `Is_New_Customer` → onboarding & contract lifecycle
2. `TotalCharges` & `MonthlyCharges` → billing weight and bill shock
3. `InternetService_Fiber optic` → network quality signal

### Phase 7 — Financial Impact & Retention Strategy Simulation
Simulated two retention strategies applied to the model's flagged churners. Financial impact calculated on an **annualized basis** (`MonthlyCharges × 12`):

| Strategy | Offer | Assumed Retention Rate | Cost Model |
|----------|-------|----------------------|------------|
| **Strategy A** | 20% Annual Discount | 30% | 20% revenue sacrifice on targeted customers |
| **Strategy B** | Free Tech Support + Online Security | 20% | $120/customer/year (fixed operational cost) |

**Conclusion:** Strategy B yields a higher net ROI despite a lower success rate, because the fixed cost per customer is significantly lower than a flat revenue discount.

### Phase 8 — Executive Dashboard & Strategy Roadmap
Business-facing visual layer built with audience-centric design principles — no ML jargon, no ROC curves. Focus on controllable behavioral drivers.

**3-Phase Prioritized Roadmap:**
- **0–30 Days:** Human-led outreach to top 500 highest-risk, highest-value accounts → offer 6 months of free Tech Support/Security
- **30–90 Days:** Automated "Lock-in Upgrade" email campaign targeting Month-to-Month customers → offer 1 month free in exchange for a 1-year contract
- **90+ Days:** Structural prevention — "Step-Up Pricing" model + 90-Day White-Glove Onboarding program for all new customers

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python 3.14.4 |
| Data Manipulation | Pandas 3.0.2 |
| Visualization | Matplotlib 3.10.8, Seaborn 0.13.2 |
| Machine Learning | Scikit-Learn 1.8.0 |
| Class Imbalance | Imbalanced-Learn 0.14.1 (SMOTE) |
| Presentation | Microsoft PowerPoint |

---

## 📊 Results Summary

| Model | AUC | Recall (Churn) | F1 (Churn) |
|-------|-----|----------------|------------|
| Logistic Regression | ~0.84 | High | Moderate |
| **Random Forest ✅** | **~0.84** | **Balanced** | **Best** |

> Random Forest recommended for deployment due to optimal Precision/Recall balance, minimizing wasted retention spend on false positives.

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/GitZi-mad/Telco-Customer-Churn-ML-Pipeline.git
cd Telco-Customer-Churn-ML-Pipeline

# Install dependencies
pip install pandas matplotlib seaborn scikit-learn imbalanced-learn jupyterlab

# Launch the notebook
jupyter lab Final_Project.ipynb
```

Run cells sequentially from Phase 1 through Phase 8. The engineered dataset (`Telco_Churn_Engineered_Ready.csv`) is the output of Phase 4 and can be loaded directly to skip preprocessing.

---

## 📁 Key Outputs

- **`Final_Project.ipynb`** — Full reproducible pipeline with documented assumptions, visualizations, model training, evaluation, and executive memo
- **`Telco_Churn_Engineered_Ready.csv`** — Cleaned, encoded, and feature-engineered dataset ready for modeling
- **`Telco_Churn_Executive_Presentation.pptx`** — Business-facing deck targeting non-technical stakeholders (CMO / Customer Success leadership)

---

## 👤 Author

**Ziad** · Computer Science, Faculty of Science, Ain Shams University  
AI Advanced Data Analyst Track — Global Knowledge × Orange Egypt  
GitHub: [@GitZi-mad](https://github.com/GitZi-mad)
