# Bank GoodCredit — Client Credit Risk Prediction Project

**Project type:** Client project  
**Client:** Bank GoodCredit  
**Domain:** Banking / Credit Risk Analytics  
**Assessment result:** **75/100 — B Grade**

## Project overview

This project was completed as a client-focused data science assignment for Bank GoodCredit. The business objective was to predict the creditworthiness of existing credit-card customers and help the bank identify customers with a higher likelihood of credit default.

The target variable is `Bad_label`:

- `0` — Good credit history
- `1` — Bad credit history (30 DPD+)

The work uses three customer data sources:

- `Cust_Account` — historical account, balance, credit-limit and payment information.
- `Cust_Enquiry` — historical credit enquiry information, including enquiry purpose and amount.
- `Cust_Demographics` — customer demographic/application attributes and the target label.

## Client deliverables

The project was structured around the three deliverables requested in the client brief:

1. **Exploratory data analysis:** identify patterns, data-quality issues and class distribution, and document the decisions taken from the findings.
2. **Feature matrix:** create customer-level predictors, document the selected inputs and examine feature importance/gain.
3. **Model evaluation:** compare model performance using ROC-AUC and Gini, and assess risk separation through decile rank ordering.

## Methodology

The notebook documents the end-to-end workflow, including:

1. Loading the three source tables from MySQL.
2. Reviewing data types, missing values, duplicate records and target distribution.
3. Cleaning and preparing account and enquiry data.
4. Aggregating account and enquiry history at customer level.
5. Joining the engineered customer-level features with the demographics data.
6. Preparing numerical and categorical inputs using imputation and encoding pipelines.
7. Training and comparing Logistic Regression, Random Forest, tuned Random Forest and XGBoost models.
8. Reviewing feature importance and evaluating model performance against the client's benchmark.

## Results

The final written evaluation in the notebook reports the following results for the selected Random Forest model:

| Metric | Result |
|---|---:|
| ROC-AUC | 0.6829 |
| Gini coefficient | 36.58 |
| Client benchmark Gini | 37.90 |
| Difference from benchmark | -1.32 Gini points |

The model did **not** exceed the client's benchmark. The notebook's decile analysis reports a higher observed bad-customer rate in the highest-risk decile than in the lowest-risk decile, indicating useful risk differentiation, although the rank ordering was not perfectly monotonic across all deciles.

The notebook also records a substantial target-class imbalance: approximately 95.8% good customers and 4.2% bad customers. This informed the use of stratified splitting and evaluation metrics beyond accuracy.

## Assessment

**Final project assessment: 75/100 (B Grade).** This is the grade received for the client project and is included here as the project's assessment outcome; it is not a model-performance metric.

## Repository structure

```text
Bank_GoodCredit_Credit_Risk_Portfolio/
├── notebooks/
│   └── Bank_GoodCredit_Credit_Risk_Model.ipynb
├── project_brief/
│   └── README.md
├── requirements.txt
└── README.md
```

## Tools and libraries

- Python
- Pandas and NumPy
- SQLAlchemy and PyMySQL
- Scikit-learn
- XGBoost
- Matplotlib and Seaborn
- Jupyter Notebook
- MySQL

Install the listed Python dependencies with:

```bash
pip install -r requirements.txt
```

## Running the notebook

1. Ensure you have authorized access to the Bank GoodCredit MySQL database.
2. Install the dependencies listed in `requirements.txt`.
3. Open `notebooks/Bank_GoodCredit_Credit_Risk_Model.ipynb` in Jupyter.
4. Run the notebook cells in order and provide the database password when prompted.

The notebook includes the database host and username used in the original project environment. Database access is not included with this repository; valid authorization and credentials are required to execute the data-loading cells.

## Confidentiality and responsible sharing

This is a client project. The original case brief is marked proprietary and confidential and contains database connection details, so it is **not included** in this portfolio package. The source customer data is also not redistributed.

Before publishing this repository publicly, confirm that you have the client's/institution's permission to share the notebook. Review saved notebook outputs for customer-level or confidential information. Keep the repository private if that permission has not been granted.

## Project file integrity

The original Jupyter notebook has been included without changing its code. The README and supporting portfolio files are separate documentation; no model code has been rewritten as part of preparing this folder for GitHub.
