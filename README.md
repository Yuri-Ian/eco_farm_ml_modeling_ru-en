# 🐄 EcoFarm: Predicting Milk Yield and Taste with ML

## 📖 Project Description
End-to-end ML analysis for a dairy farm purchasing program. The notebook predicts annual milk yield (linear regression) and milk taste (logistic regression) from cow, sire, and pasture features. Results are used to shortlist cows with high productivity and a high probability of tasty milk.

---

## 🎯 Project Goal
To build a reproducible pipeline that:
- Cleans and preprocesses raw farm data.  
- Explores distributions and correlations.  
- Trains and compares linear regression models for yield.  
- Trains a logistic regression model for taste.  
- Applies models to a purchase list to select candidates by thresholds.  

---

## 🛠️ Tasks
- Perform data audit and preprocessing (types, duplicates, anomalies).  
- Conduct EDA and correlation analysis; detect multicollinearity.  
- Engineer features for linearity (threshold binarization for SPO, EKE²).  
- Train three LinearRegression variants; evaluate by R², residuals, RMSE/MAE/MSE.  
- Train LogisticRegression; evaluate by accuracy, precision, recall, confusion matrix.  
- Tune threshold to maximize precision and reduce business risk.  
- Rank and select cows from the purchase list.  

---

## 📊 Datasets
- `ferma_main.csv` — core features: yield, feed energy, sugar–protein ratio, fat/protein, breed, pasture, age.  
- `ferma_dad.csv` — sire metadata: id, sire name.  
- `cow_buy.csv` — candidate cows for purchase (subset of features; enriched before inference).  

---

## 🔑 Major Insights
- Yield drivers: sugar–protein ratio (SPO), feed energy (EKE/EKE²), fat content; sire adds predictive power.  
- Multicollinearity among feed indicators requires adjustment; feature transforms improved model stability.  
- Logistic regression prioritizing precision eliminates costly false positives after threshold tuning.  

---

## 📈 Model Highlights
- Linear Regression (test R²):  
  - Model 1 (baseline): 0.796  
  - Model 2 (SPO binarized, EKE²): 0.820  
  - Model 3 (+ sire name): 0.833  
- Logistic Regression (default threshold): accuracy ~0.73, recall ~0.80, precision ~0.61.  
  - Precision-max threshold (~0.80) → precision 1.0, recall drops significantly.  

---

## ✅ Business Outcome
From 16 candidate cows, 3 met both criteria: yield >6000 kg/year and high probability of tasty milk.  
These represent the safest purchases. If inventory is too narrow, thresholds can be relaxed.  

Recommendations:
- Keep structured post-purchase data to improve future models.  
- Add an economic model to balance milk revenue against upkeep costs.  
- Explore advanced models (Random Forest, Gradient Boosting) for richer insights.  

---

## 📂 Repository Structure
- `eco_farm_ml_modeling_ru+en.ipynb` — full bilingual analysis with Data/Code sidenotes.   
- `README.md` — project description and results in English.
- `RU_README.md` — project description and results in English.  

---

## 📌 Notes
This notebook reflects one of my first structured ML projects. I put significant effort into documenting the reasoning behind every step, clarifying why methods were chosen and how results were validated. The focus was on transparency and structured workflow, rather than compactness. In real production projects I would use more concise text and rely on pipelines, automated preprocessing, and extended visualizations. Preserving this version shows how I pay attention to detail and communicate analytical thinking.
