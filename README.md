# 🛢️ Oil & Gas Pipeline Incident Analysis (CER Dataset)

---

## 📌 Project Title
**Geospatial and Meteorological Analysis of Substance Release Incidents in Canadian Pipelines**

---

## 📖 Overview

This project analyzes pipeline incident data provided by the **Canada Energy Regulator (CER)**. The dataset contains **723 recorded incidents (2008–2020)** involving substance releases in oil and gas pipelines and related facilities.

The main objective is to understand which **geographical and environmental factors** are associated with the probability of a substance release incident.

---

## 🎯 Research Question

> What geographical and meteorological factors are associated with pipeline incidents involving substance release?

The response variable is:

- **SubstanceRelease (Yes/No)**

The predictors include:

- Geographical variables (Province, Latitude, Longitude, population-related features)
- Operational variables (Company, Status, Release Type)
- Incident characteristics (Significant, Substance type)
- Temporal variable (Year)

---

## 📂 Dataset Description

The dataset includes **723 observations** from CER records:

- 📍 Location data (Latitude, Longitude, Province, nearest populated center)
- 🏢 Company responsible for the pipeline
- ⚠️ Incident attributes (Release type, substance type, significance)
- 📅 Year of incident
- 📊 Operational status (Closed, Submitted, Initially Submitted)
- 🧾 Free-text fields describing cause and outcome of incidents

---

## 🧪 Methodology

### 1. Exploratory Data Analysis (EDA)

Initial data exploration using `tidyverse` and `ggplot2`:

- Yearly trend of substance releases
- Province-wise incident distribution
- Company-wise incident frequency
- Impact of operational status and release type
- Substance-level breakdown

Key insight:
- Certain provinces show higher likelihood of substance release events.
- Company and location are important predictive variables.

---

### 2. Feature Engineering

We created additional variables:

- Count of reasons (`n.why.It.Happened`)
- Count of incident descriptions (`n.What.Happened`)
- Geographic clustering using **K-means on Latitude & Longitude**

Optimal clustering was selected using within-cluster variation analysis.

---

### 3. Modeling Approach

We applied **logistic regression models (GLM with logit link)** to predict:

> Probability of SubstanceRelease = Yes

### Train/Test Split
- 70% training set
- 30% testing set

---

### 4. Models Evaluated

Multiple Modles:

- Province-only model
- Year-only model
- Location (Latitude, Longitude)
- Significant incident flag
- Release type
- Status
- K-means cluster (geospatial grouping)
- Combined feature models

---

### 5. Final Model

The best performing model included:

- Latitude
- Longitude
- Year
- Province
- K-means cluster (geospatial grouping)

---

## 📊 Results

- Model performance ranged between **50% – 70% accuracy**
- Final selected model achieved approximately:

> ✅ **~70% prediction accuracy**

---

## 🧠 Key Findings

- 📍 **Geography is the strongest predictor** of substance release incidents  
- 🗺️ Provinces and spatial clustering significantly influence risk  
- 🏢 Company-level effects exist but are harder to generalize  
- 📅 Temporal trends show variation in incident frequency over years  
- ⚠️ Some variables (e.g., Release Type, Status) have limited predictive power  

---

## ⚠️ Limitations

- High-cardinality categorical variables (e.g., Company, Substance) were excluded from final models due to:
  - Class sparsity
  - Training/testing inconsistency
- Some text variables required simplification (counts instead of NLP modeling)
- Accuracy ceiling limited due to data imbalance and complexity

---

## 📁 Repository Contents

- `project3.R` → Main R script  
- `project3.Rmd` → R Markdown analysis report  
- `project3.pdf` → Final compiled report  
- `projectData.csv` → CER incident dataset  

---

## 📌 Conclusion

This study shows that **geographical and spatial factors play a key role** in predicting pipeline substance release incidents. While operational and categorical variables provide additional context, location-based modeling offers the strongest predictive signal.

---

## 📊 Tools & Libraries

- R (`glm`, `kmeans`)
- `tidyverse`
- `ggplot2`
- `ggthemes`

---
