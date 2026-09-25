# British Airways Customer Booking Prediction

## Project Overview

This project was completed as part of the British Airways Data Science Virtual Experience on Forage.

The objective was to build a machine learning model that predicts whether a customer completes a flight booking based on customer and flight-related information.

The project covers data preparation, exploratory analysis, machine learning, model evaluation, cross-validation, and feature importance analysis.

## Business Problem

Understanding which customer and booking characteristics contribute most to booking completion can help identify useful predictive signals for customer behavior and future marketing analysis.

The target variable was:

- `booking_complete = 1` — booking completed
- `booking_complete = 0` — booking not completed

The dataset contains 50,000 customer booking records.

## Dataset

The dataset contains information about customer bookings, including:

- Number of passengers
- Sales channel
- Trip type
- Purchase lead time
- Length of stay
- Flight hour
- Flight day
- Route
- Booking origin
- Extra baggage preference
- Preferred seat preference
- In-flight meal preference
- Flight duration
- Booking completion

The dataset contained no missing values.

Because the dataset is provided as part of the Forage simulation, the original CSV file is not included in this repository.

## Methodology

The analysis followed these steps:

1. Loaded and inspected the dataset.
2. Checked the structure and descriptive statistics.
3. Examined the distribution of the target variable.
4. Separated features from the target variable.
5. Identified categorical and numerical variables.
6. Applied one-hot encoding to categorical variables.
7. Split the data into training and test sets using stratified sampling.
8. Trained a Random Forest Classifier.
9. Used class balancing to account for the imbalanced target variable.
10. Evaluated the model using multiple classification metrics.
11. Performed stratified 5-fold cross-validation.
12. Analyzed variable contribution using permutation importance.

## Machine Learning Model

A Random Forest Classifier was used because it can model nonlinear relationships and provides feature importance information.

### Model Configuration

- 200 decision trees
- `class_weight="balanced"`
- `random_state=42`
- Stratified train/test split
- 5-fold stratified cross-validation

## Model Performance

### Test Set

| Metric | Result |
|---|---:|
| Accuracy | 82.24% |
| Precision | 40.00% |
| Recall | 37.43% |
| F1-score | 38.67% |
| ROC-AUC | 79.40% |

### 5-Fold Cross-Validation

| Metric | Mean ± Standard Deviation |
|---|---:|
| Accuracy | 82.30% ± 0.50% |
| Precision | 39.94% ± 1.76% |
| Recall | 36.34% ± 1.30% |
| F1-score | 38.05% ± 1.46% |
| ROC-AUC | 78.14% ± 0.39% |

The relatively small variation across cross-validation folds indicates that model performance was reasonably consistent across the training data.

Accuracy was not considered in isolation because only 14.96% of customers in the dataset completed a booking.

## Feature Importance

Permutation importance was used to examine how much the model's ROC-AUC changed when individual variables were randomly shuffled.

The strongest predictive variables were:

1. Booking origin
2. Route
3. Length of stay
4. Sales channel
5. Wants extra baggage

These variables provided the strongest predictive contribution to the model's performance.

Feature importance represents the model's reliance on these variables for prediction and should not be interpreted as evidence that these variables directly cause customers to make bookings.

## Confusion Matrix

The model produced the following results on the test set:

| Actual | Predicted No Booking | Predicted Booking |
|---|---:|---:|
| No Booking | 7,664 | 840 |
| Booking | 936 | 560 |

The model correctly identified 560 completed bookings while missing 936 actual bookings.

## Key Findings

- Booking completion represented 14.96% of records in the dataset.
- Booking origin was the strongest variable according to permutation importance.
- Route was the second strongest predictive variable.
- Length of stay and sales channel also contributed meaningful predictive information.
- The Random Forest achieved a test ROC-AUC of 79.40%.
- Cross-validation produced a similar ROC-AUC of 78.14%.
- Feature importance identifies predictive contribution rather than causation.

## Project Visualizations

### Booking Distribution

![Booking Distribution](images/booking_distribution.png)

### Feature Importance

![Feature Importance](images/feature_importance.png)

### Confusion Matrix

![Confusion Matrix](images/confusion_matrix.png)

## Project Files

- `notebooks/` — Jupyter Notebook containing the complete analysis
- `images/` — Project visualizations
- `presentation/` — Final British Airways presentation
- `requirements.txt` — Python dependencies
- `README.md` — Project documentation

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Random Forest
- One-Hot Encoding
- Cross-Validation
- Permutation Importance
- Classification Metrics

## Certification / Experience

Completed as part of the British Airways Data Science Virtual Experience on Forage.

## Author

Ntlakuso Nkuna
