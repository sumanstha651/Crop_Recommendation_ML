# Crop Recommendation Using Machine Learning

## 1. Project Description

This project develops a machine learning-based crop recommendation system using soil and climatic parameters.

The system predicts the most suitable crop based on seven input features:

* Nitrogen (N)
* Phosphorus (P)
* Potassium (K)
* Temperature
* Humidity
* Soil pH
* Rainfall

The dataset contains **2,200 samples across 22 crop classes**. Several machine learning classification algorithms were trained and evaluated, followed by cross-validation and hyperparameter tuning.

The final model is a **Random Forest Classifier**, which achieved **99.55% accuracy on the held-out test set**.

---

## 2. Dataset

The project uses a crop recommendation dataset containing 2,200 observations and 22 crop classes.

### Features

| Feature     | Description                |
| ----------- | -------------------------- |
| N           | Nitrogen content in soil   |
| P           | Phosphorus content in soil |
| K           | Potassium content in soil  |
| Temperature | Temperature in °C          |
| Humidity    | Relative humidity (%)      |
| pH          | Soil pH value              |
| Rainfall    | Rainfall in mm             |
| Label       | Recommended crop           |

The dataset is stored in the `data/` directory.

---

## 3. Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the dataset and identify patterns in the soil and climatic features.

The EDA includes:

* Dataset structure and summary statistics
* Missing-value analysis
* Duplicate-value analysis
* Crop/class distribution
* Numerical feature distributions
* Correlation analysis
* Average N, P, and K values by crop
* Feature distributions across different crops
* Outlier analysis using boxplots

The complete EDA notebook is available at:

`notebooks/01_EDA.ipynb`

---

## 4. Machine Learning Models

The following classification algorithms were evaluated:

* Logistic Regression
* Decision Tree
* Random Forest
* Support Vector Machine (SVM)
* K-Nearest Neighbors (KNN)

The dataset was divided using an **80/20 stratified train-test split** with `random_state=42`.

Feature scaling was applied where appropriate. Tree-based models were trained using the original feature values, while scaling was incorporated into pipelines for models that require it.

---

## 5. Model Evaluation

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* Classification Report
* Confusion Matrix

### Cross-Validation

A **5-fold Stratified Cross-Validation** strategy was used to evaluate model performance more reliably.

### Hyperparameter Tuning

`GridSearchCV` was used to optimize the hyperparameters of all evaluated models.

The tuned Random Forest achieved the highest cross-validation accuracy:

**Best CV Accuracy: 99.60%**

The best Random Forest configuration was:

* `n_estimators = 200`
* `max_depth = None`
* `min_samples_split = 5`
* `min_samples_leaf = 1`

---

## 6. Final Model

Based on cross-validation and hyperparameter tuning, **Random Forest** was selected as the final model.

The final model was evaluated on the held-out test set.

| Metric    |  Score |
| --------- | -----: |
| Accuracy  | 99.55% |
| Precision | 99.57% |
| Recall    | 99.55% |
| F1-Score  | 99.55% |

These results represent performance on the project's held-out test set and should not be interpreted as guaranteed real-world accuracy.

---

## 7. Feature Importance

Feature importance from the final Random Forest model indicates the relative contribution of the input features to the model's predictions.

The features ranked by importance were:

| Feature     | Importance |
| ----------- | ---------: |
| Rainfall    |     0.2208 |
| Humidity    |     0.2202 |
| K           |     0.1783 |
| P           |     0.1488 |
| N           |     0.1067 |
| Temperature |     0.0746 |
| pH          |     0.0507 |

Rainfall and humidity had the highest feature importance in the trained Random Forest model.

---

## 8. Crop Recommendation System

A crop recommendation function was developed using the final trained model.

The system accepts the following inputs:

```text
Nitrogen (N)
Phosphorus (P)
Potassium (K)
Temperature
Humidity
Soil pH
Rainfall
```

The trained Random Forest model then predicts the recommended crop.

Example:

```python
recommended_crop = recommend_crop(
    N=90,
    P=42,
    K=43,
    temperature=20.8,
    humidity=82,
    ph=6.5,
    rainfall=202
)

print("Recommended Crop:", recommended_crop)
```

Output:

```text
Recommended Crop: rice
```

An interactive version is also included in the model development notebook, allowing users to enter their own soil and climatic values.

---

## 9. Saved Models

The trained model and label encoder are saved in the `models/` directory:

```text
models/
├── final_crop_recommendation_model.pkl
└── crop_label_encoder.pkl
```

The Random Forest model is stored using `joblib` and can be loaded later for making predictions without retraining the model.

---

## 10. Repository Structure

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
├── models/
│   ├── final_crop_recommendation_model.pkl
│   └── crop_label_encoder.pkl
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   └── 02_Model_Development.ipynb
│
└── result/
    └── [EDA and model evaluation results]
```

---

## 11. Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Joblib
* Jupyter Notebook

---

## 12. How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/sumanstha651/Crop_Recommendation_ML.git
```

### 2. Navigate to the project directory

```bash
cd Crop_Recommendation_ML
```

### 3. Create a virtual environment

```bash
python -m venv .venv
```

### 4. Activate the environment

On Windows:

```bash
.venv\Scripts\activate
```

### 5. Install the required packages

```bash
pip install -r requirements.txt
```

### 6. Open the notebooks

Open:

```text
notebooks/01_EDA.ipynb
notebooks/02_Model_Development.ipynb
```

Run the notebooks from top to bottom.

---

## 13. Project Status

**Status: Completed**

The project includes:

* Dataset preprocessing
* Exploratory Data Analysis
* Multiple machine learning models
* Model evaluation
* 5-fold cross-validation
* Hyperparameter tuning
* Final model selection
* Feature importance analysis
* Crop recommendation function
* Interactive crop recommendation
* Saved trained model and label encoder
