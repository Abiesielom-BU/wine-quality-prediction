# 🍷 Wine Quality Prediction — Statistical Analysis & Linear Regression

**Course:** DX601 — Mathematical Foundations of Data Science  
**Program:** M.S. in Data Science, Boston University  
**Dataset:** [UCI Wine Quality Dataset (White Wine)](https://archive.ics.uci.edu/dataset/186/wine+quality) — 4,898 records, 11 features  

---

## 📌 Project Overview

This project applies statistical analysis, feature exploration, and machine learning to predict the quality rating of white wines based on their chemical properties. The analysis covers distribution modeling, feature correlation, linear regression, principal component analysis (PCA), and outlier detection.

---

## 🎯 Key Findings

| Analysis | Result |
|---|---|
| Best multi-feature model MSE | **0.5631** |
| Best single-feature model MSE | **0.6354** (alcohol content) |
| MSE improvement using all features | **10.4%** over best single predictor |
| PCA variance explained (first half of components) | **~72.8%** |
| PCA-based model MSE | **0.644** |
| Most correlated feature pair | **Residual sugar & Density** (r = 0.839) |
| Strongest quality predictor | **Alcohol content** |

---

## 📊 Analysis Breakdown

### 1. Data Loading & Exploration
- Loaded the white wine subset from UCI/PMLB
- Displayed random sample and documented all 12 columns in plain language

### 2. Distribution Analysis
- Plotted histograms for all 12 features
- Identified distribution types per feature:
  - **Normal/Bell-shaped:** pH, density
  - **Right-skewed:** residual sugar, chlorides, volatile acidity, citric acid
  - **Discrete:** target (quality ratings 3–9, most wines rated 5 or 6)

### 3. Feature Independence
- Scatter plotted each input feature against the quality target
- Found that **volatile acidity**, **chlorides**, and **total sulfur dioxide** show negative relationships with quality
- **Alcohol** shows the strongest positive relationship with quality

### 4. Linear Regression — All Features
- Built an OLS regression model using all 11 input columns
- Achieved **MSE of 0.5631** (~0.75 quality points from actual on average)
- Model performs well for average-quality wines but struggles at quality extremes

### 5. Single-Feature Model Comparison
- Tested each feature individually as a predictor
- **Alcohol** was the best single predictor (MSE: 0.6354)
- Full-feature model outperformed by **10.4%**, confirming multi-feature value

### 6. Feature Dependency & Threshold Split
- Identified strong dependency between **residual sugar** and **density**
- Split at threshold t=15: wines with high sugar showed clearly higher and more spread density values
- Confirmed the two variables are not independent

### 7. Principal Component Analysis (PCA)
- Standardized all features before applying PCA
- First 5 components (half of 11) explained **~72.8%** of total variance
- PCA-based regression MSE: **0.644** — slightly worse than full-feature model, but confirms most signal is captured in first half of components
- PC1 groups **density and residual sugar** together due to their high correlation (r=0.839)

### 8. Outlier Detection
- Used Euclidean distance from origin in PCA space (PC1² + PC2²)
- Identified **row 2781** as the outlier — residual sugar value of **65.8** (typical range: 1–15)
- Confirmed visually via PCA scatter plot and boxplot

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data loading and manipulation |
| NumPy | Numerical computations |
| Matplotlib | Data visualizations |
| Scikit-learn | Linear regression, PCA |
| SciPy | Statistical analysis |

---

## 📁 Project Structure

```
wine-quality-prediction/
│
├── Dx601Final_Project.ipynb   # Full analysis notebook
├── README.md                  # Project documentation
└── wine_quality_white.tsv.gz  # Dataset (download from UCI/PMLB)
```

---

## 🚀 How to Run

1. Clone the repository
```bash
git clone https://github.com/yourusername/wine-quality-prediction.git
cd wine-quality-prediction
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib scikit-learn scipy
```

3. Download the dataset from [PMLB](https://github.com/EpistasisLab/pmlb/tree/master/datasets/wine_quality_white) and place `wine_quality_white.tsv.gz` in the project folder

4. Launch Jupyter Notebook
```bash
jupyter notebook Dx601Final_Project.ipynb
```

---

## 📚 Dataset Features

| Feature | Description |
|---|---|
| fixed acidity | Non-volatile acids that affect wine taste |
| volatile acidity | Evaporable acids that affect wine aroma |
| citric acid | Adds freshness to wine flavor |
| residual sugar | Sugar remaining after fermentation |
| chlorides | Salt content in wine |
| free sulfur dioxide | SO₂ that protects wine from spoilage |
| total sulfur dioxide | Total SO₂ present in wine |
| density | Weight of wine relative to water |
| pH | Acidity level of the wine |
| sulphates | Preservation compounds affecting taste |
| alcohol | Alcohol percentage by volume |
| **target** | **Quality rating (3–9 scale)** |

---

*Boston University — M.S. in Data Science | DX601 Final Project*
