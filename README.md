# 📊 Residual Analysis on Household Expenditure Data

## 📌 Objective

This project performs **residual analysis** on household consumption and income data. The aim is to validate regression assumptions and identify model improvements.

Key goals:
1. Plot residuals and test assumptions of **normality**, **homoscedasticity**, and **independence**.
2. Apply **remedial measures** when assumptions are violated.
3. Detect **influential data points** through model perturbation.

---

## 🧪 Dataset

The dataset contains the **annual expenditure and disposable income** for 30 households in India.

- **Dependent variable (Y):** Expenditure  
- **Independent variable (X):** Income

---

## 🔍 Methodology & Analysis

### 1. 📈 Exploratory Data Analysis
- Scatterplot matrix visualizes the relationship between income and expenditure.
- Strong **linear correlation** observed.

### 2. 📉 Simple Linear Regression
- Model:  
  \[
  \hat{Expenditure} = 2799 + 0.7327 \times Income
  \]
- **R² = 0.89** → Income explains 89% of the variability in expenditure.

### 3. 📊 Residual Diagnostics
#### ✅ Normality
- **Q-Q plot** suggests residuals are approximately normally distributed.
- **Shapiro-Wilk Test**: p = 0.868 → Fail to reject H₀ → Residuals are normal.

#### ❌ Homoscedasticity
- **Residuals vs Fitted Plot**: Funnel shape observed → Suggests heteroscedasticity.
- **Breusch-Pagan Test**: p = 0.000745 → Reject H₀ → Residuals are heteroscedastic.

#### ✅ Transformation
- Attempted:
  - `log(Y)`: Still heteroscedastic
  - `sqrt(Y)`: Still heteroscedastic
  - `1/Y`: p = 0.3009 → Homoscedasticity achieved 🎉

### 4. 🔁 Autocorrelation
- **Durbin-Watson Test**: p < 0.05, D = 0.31 < D_L → Residuals are autocorrelated.

### 5. 🧪 Outlier and Influence Detection
- Added an unusual observation `(60000, 21000)`
- **Drastic drop in R²** from 0.89 to 0.29 → High influence confirmed.
- Regression line slope changed significantly → Confirms **influential outlier**.

---

## ✅ Conclusion

- A **linear model** fits the data well initially.
- Residuals are **normal but heteroscedastic**.
- **Inverse transformation** resolves heteroscedasticity.
- **Autocorrelation** is present → May need time-series modeling for improvement.
- The model is **sensitive to influential points**.

---

## 📂 Files Included

- `residual_analysis.Rmd` – Full R Markdown source with code, analysis, and interpretations.
- `home expenditure.xlsx` – Input dataset .

---

## 🛠 Tools & Libraries

- **R** with `lm()`, `bptest()`, `shapiro.test()`, `dwtest()`
- `ggplot2`, `car`, `lmtest`, and base R plotting

---


## 👨‍💻 Author

- *Angel Lal*
🔗 [View the rendered R project on RPubs](https://rpubs.com/angallal/1313133)
