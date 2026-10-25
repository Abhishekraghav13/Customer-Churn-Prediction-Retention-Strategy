
# Customer Churn Prediction & Retention Strategy
### An End-to-End Machine Learning Project Using Telecom Customer Data

## Project overview
This project explores how machine learning can identify customers with a higher likelihood of churn and help a retention team prioritize outreach under a limited campaign budget.

The notebook covers data quality checks, exploratory analysis, preprocessing, model comparison, threshold and fixed-budget evaluation, a final held-out test assessment, calibration, subgroup diagnostics, and a proposed retention experiment.

## Business problem
Customer churn can reduce recurring revenue and increase replacement costs. The practical goal is not only to estimate churn risk, but to explore how a business could prioritize a limited number of customers for retention outreach.

## Project objectives
- Clean and validate the Telco Customer Churn dataset.
- Explore churn patterns across customer and service characteristics.
- Build a preprocessing and modeling pipeline.
- Compare a baseline with classification models.
- Evaluate model performance using metrics including ROC-AUC, average precision, precision, recall, and F1.
- Assess ranking performance when outreach capacity is limited to 300 customers.
- Document model limitations, calibration, and subgroup diagnostics.
- Propose a randomized experiment to measure whether a retention offer actually changes churn outcomes.

## Repository contents
- `Customer_Churn_Prediction_&_Retention_Strategy.ipynb` — main analysis notebook.
- `requirements.txt` — Python package dependencies.
- `executive_summary.md` — concise project and results summary.
- `images/` — optional charts exported from the notebook for quick viewing on GitHub.

## Dataset
This project uses the IBM Telco Customer Churn sample dataset, commonly distributed as `WA_Fn-UseC_-Telco-Customer-Churn.csv`.

Obtain the CSV from the dataset's original or authorized source. Do not commit the raw dataset unless its applicable license and terms explicitly permit redistribution. The notebook's default workflow asks you to upload the CSV in Google Colab.

## How to run
1. Open the notebook in Google Colab.
2. Upload `WA_Fn-UseC_-Telco-Customer-Churn.csv` when prompted.
3. Run the notebook from top to bottom.
4. Check the output and any warnings before relying on results.

For a local environment, install the dependencies with:

```bash
pip install -r requirements.txt
```

The notebook may use Google Colab's upload helper for its default data-loading path; if running locally, adapt that cell to load the CSV from your local path.

## Main findings
- Churn is substantially higher among month-to-month customers than among customers on longer-term contracts.
- Churn rates are higher among customers with shorter tenure.
- Logistic Regression provides a useful, interpretable baseline for ranking churn risk.
- In the held-out test set, the selected reduced, untuned Logistic Regression model achieved ROC-AUC of approximately **0.843** and average precision of approximately **0.652**.
- When ranking customers by predicted risk, the top 300 test customers included 180 actual churners: precision@300 was **0.600**, recall@300 was approximately **0.641**, and lift was approximately **2.26×** the test-set base churn rate.

These metrics describe prediction and ranking performance. They do **not** show that contacting those customers would prevent 180 churns.

## Modeling and evaluation notes
- The final reported test metrics belong to the reduced, untuned Logistic Regression model without `TotalCharges`.
- A tuned Logistic Regression model was evaluated on validation data, but was not the model used for the final test metrics.
- The dataset is a historical snapshot without a clearly defined prediction timestamp or future churn horizon. The random split therefore supports internal comparison, but does not prove production-style future prediction.
- The blank `TotalCharges` values for 11 zero-tenure customers were filled with zero based on an explicit, documented assumption.
- The A/B test section is a hypothetical proposal. Its effect size and sample-size assumptions are planning assumptions, not results measured from this dataset.

## Important distinction: prediction vs. retention impact
A churn model estimates risk. It does not identify by itself which customers can be persuaded to stay. Measuring retention impact requires a well-designed experiment or other causal evaluation. Any real campaign should also account for offer costs, customer value, eligibility, and potential customer impact.

## Limitations
- No explicit prediction date or forward-looking churn horizon is available.
- The dataset is a sample dataset and may not represent a current telecom customer base.
- Model scores and subgroup metrics can vary across samples.
- Subgroup comparisons are diagnostic, not by themselves proof of fairness or unfairness.
- Campaign effectiveness cannot be inferred from model ranking alone.

## Tools
Python, pandas, NumPy, Matplotlib, and scikit-learn.

## Author
Add your name or portfolio link here if you want to identify yourself publicly.
