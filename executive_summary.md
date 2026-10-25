# Executive Summary
## Customer Churn Prediction & Retention Strategy

### Objective
Build a machine-learning workflow to estimate churn risk and evaluate whether model rankings could help prioritize a limited retention outreach campaign.

### Approach
The project cleans the IBM Telco Customer Churn sample data, explores churn patterns, uses a stratified train/validation/test split, and compares baseline and machine-learning approaches. Preprocessing is performed through a pipeline with numeric imputation/scaling and categorical imputation/one-hot encoding. Model evaluation includes classification metrics, ROC-AUC, average precision, threshold comparisons, and a fixed-budget top-300 ranking analysis.

### Key findings
- Churn is higher among month-to-month customers and customers with shorter tenure.
- The selected reduced, untuned Logistic Regression model achieved test ROC-AUC of approximately **0.843** and average precision of approximately **0.652**.
- Of the top 300 customers ranked by predicted risk in the test set, 180 were actual churners. Precision@300 was **60.0%**, recall@300 was approximately **64.1%**, and lift was approximately **2.26×** the overall test churn rate.

### Interpretation
The model appears useful for ranking customers for further review under a fixed outreach capacity. However, the result does not prove that a retention offer would save these customers. Predictive risk and treatment responsiveness are different questions.

### Model-selection transparency
The final test metrics are for the reduced, untuned Logistic Regression model without `TotalCharges`. A tuned version was evaluated on validation data but was not selected for the final test assessment because it did not improve the project's fixed-budget ranking objective in validation. The small differences should not be interpreted as proof of universal superiority.

### Assumptions and limitations
- Eleven blank `TotalCharges` values occurred for customers with zero tenure and no recorded churn. These were set to zero under a documented assumption.
- The dataset does not specify a clear prediction timestamp or future prediction horizon.
- The retention A/B test and its effect-size/sample-size assumptions are hypothetical.
- Subgroup metrics are diagnostic and require careful interpretation.
- A randomized experiment is needed to estimate whether a retention intervention causally reduces churn.
