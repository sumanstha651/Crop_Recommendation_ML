# Crop Recommendation Using Machine Learning

## 1. Project Description

This project develops a machine learning-based crop recommendation system using soil and climatic parameters.

The dataset contains 2,200 samples across 22 crop classes. The features include nitrogen (N), phosphorus (P), potassium (K), temperature, humidity, pH, and rainfall.

The project currently focuses on exploratory data analysis (EDA) and preliminary machine learning model development for the midterm stage.

## 2. Dataset

The dataset contains the following features:

- N — Nitrogen
- P — Phosphorus
- K — Potassium
- Temperature
- Humidity
- pH
- Rainfall
- Label — Recommended crop

There are 2,200 observations and 22 crop classes.

The dataset is included in the `data/` directory.

## 3. Exploratory Data Analysis

The EDA includes:

- Dataset structure and summary statistics
- Missing-value analysis
- Crop/class distribution
- Numerical feature distributions
- Correlation analysis
- Average N, P, and K values by crop
- Feature distributions across different crops

The complete EDA is available in:

`notebooks/01_EDA.ipynb`

## 4. Machine Learning Models

The following models were evaluated during the preliminary model development:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)

The dataset was divided into training and testing sets using an 80/20 stratified split with `random_state=42`.

The complete model development is available in:

`notebooks/02_Model_Development.ipynb`

## 5. Preliminary Results

The preliminary evaluation compares the models using classification performance metrics.

Random Forest achieved the highest preliminary test accuracy among the evaluated models, at approximately 99.55%.

Detailed results are available in:

`notebooks/preliminary_model_results.csv`

These are preliminary midterm results. Further model tuning and evaluation will be performed in later stages of the project.

## 6. Repository Structure

```text
Crop_Recommendation_ML/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── Crop_recommendation.csv
│
└── notebooks/
    ├── 01_EDA.ipynb
    ├── 02_Model_Development.ipynb
    └── preliminary_model_results.csv
