# Distributed Data Analysis and Mining – US Accidents

## Overview
This project focuses on the analysis of the US Accidents dataset (2016–2023), containing approximately 7.7 million traffic accident records collected across 49 U.S. states.

The objective is to analyze patterns of traffic accidents and develop predictive models for accident severity and duration using a distributed computing approach based on PySpark.

## Dataset
The dataset includes 46 features describing:
- temporal aspects (time of accident, duration)
- geographical information (coordinates, state, city)
- weather conditions (temperature, visibility, precipitation, etc.)
- road infrastructure and traffic elements

The data were collected from multiple real-time sources such as traffic sensors, authorities and APIs. :contentReference[oaicite:0]{index=0}

---

## Data Preparation

### Cleaning
- Removal of non-informative records (missing key weather variables)
- Removal of duplicate records
- Feature selection and reduction of redundant variables

### Outlier Detection
- Detection and correction of unrealistic values in meteorological variables
- Use of domain-based rules (e.g. precipitation, visibility, temperature)

### Missing Values Handling
- Context-aware imputation using grouped statistics (State, Month, weather conditions)
- Creation of engineered categorical features (e.g. `weather_grouped`)

---

## Exploratory Analysis

The analysis was driven by three main research questions:

- **Temporal patterns:** accidents peak during commuting hours (morning and late afternoon)
- **Geospatial patterns:** most accidents are concentrated in highly populated states (e.g. California, Florida, Texas)
- **COVID-19 impact:** a clear reduction in accidents was observed during 2020 lockdown periods :contentReference[oaicite:1]{index=1}

---

## Clustering

Goal: identify typical accident profiles.

- Algorithms used:
  - K-Means
  - Bisecting K-Means

- Feature engineering:
  - temporal features (Hour, Month, Weekday)
  - meteorological variables
  - spatial information

- Result:
  - 3 main clusters identified
  - K-Means chosen as best model (Silhouette ≈ 0.49)

Clusters represent:
- frequent and regular accidents
- weather-related complex scenarios
- rare and extreme events

---

## Classification

Task: predict accident **Severity** (multi-class classification)

Models used:
- Decision Tree
- Random Forest
- Logistic Regression

Key aspects:
- strong class imbalance in the dataset
- comparison between:
  - imbalanced data
  - oversampling
  - undersampling

Result:
- Decision Tree achieved the best performance
- undersampling improved fairness and minority class prediction

---

## Regression

Task: predict accident **duration**

Models:
- Decision Tree
- Random Forest

Findings:
- weak linear correlations between features and duration
- better performance achieved using non-linear models
- best model reached R² ≈ 0.50 with enriched features

---

## Explainability (XAI)

- LIME used to interpret model predictions
- analysis performed on both:
  - full-feature model
  - reduced-feature model

Goal:
- understand which features influence severity predictions

---

## Technologies

- Python
- PySpark (distributed processing)
- Machine Learning (MLlib)
- Jupyter Notebook

---
