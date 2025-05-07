# ✈️ Airline Review Classification Project

## 📌 Objective

The goal of this project is to build a **binary classification model** that predicts whether a passenger would **recommend an airline** based on various features from their review. The target variable is `recommended`, which indicates whether the passenger recommended the airline (`yes` or `no`). By accurately predicting passenger satisfaction, this model can assist airlines in identifying areas of improvement and understanding customer behavior patterns.

---

## 🧾 Dataset Overview

The dataset contains over **130,000 airline reviews** submitted by passengers. However, after removing rows with missing target labels and cleaning the data, approximately **66,000 reviews** are used for modeling.

### Key Features:

- **Categorical Variables**:  
  - `airline`: Name of the airline (81+ unique values)  
  - `cabin`: Class of travel (Economy, Business, etc.)  
  - `traveller_type`: Purpose of travel (Business, Leisure, etc.)

- **Numerical Ratings**:  
  - `overall`: Overall rating (1–10)  
  - `seat_comfort`, `cabin_service`, `food_bev`, `entertainment`, `ground_service`, `value_for_money`: Sub-ratings for flight experience

- **Text Field**:  
  - `customer_review` (Dropped in this project for simplicity)

- **Dropped Columns**:  
  Features such as `aircraft`, `route`, `author`, `date_flown`, and `review_date` were removed due to high missing values or limited predictive value.

---

## 🧼 Data Cleaning and Imputation

Several steps were taken to prepare the data for classification:

1. **Removed rows** with missing target values in `recommended`.
2. **Mapped target** from `'yes'/'no'` to binary `1/0`.
3. **Imputed missing numerical ratings** using column-wise mean.
4. **Categorical columns** with missing data were imputed using mode or random imputation for diversity.
5. **Dropped high-cardinality or sparse columns** like `aircraft` and `customer_review` to avoid model noise and memory inefficiency.

---

## 🔢 Encoding Strategy

- **Airline Encoding**: Given the high cardinality of the `airline` column, simple **Label Encoding** was used. This is suitable for **tree-based models** such as Random Forest or XGBoost, which do not assume ordinal relationships between encoded values.
- **Other Categorical Variables**: Categorical columns like `cabin` and `traveller_type` were also label-encoded for compatibility with modeling pipelines.

---

## 🧠 Modeling Approach

The primary goal is to classify whether a passenger **recommends an airline** or not. The dataset exhibits some class imbalance, but it's manageable using stratified train/test splits or class weights in modeling.

Planned models for experimentation include:

- **Random Forest Classifier**
- **XGBoost Classifier**
- **Logistic Regression** (if categorical encoding is adjusted)

These models will be evaluated using metrics such as **accuracy, precision, recall, F1-score, and ROC-AUC**.

---

## 📈 Impact and Use Cases

This classification system can provide actionable insights for airline companies, such as:

- Identifying **critical service factors** that influence customer satisfaction
- Segmenting customer behavior based on cabin class or travel purpose
- Reducing negative experiences by predicting and addressing dissatisfaction early

---
