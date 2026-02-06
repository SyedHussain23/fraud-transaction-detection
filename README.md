# 💳 Fraud Transaction Detection

Fraud detection is a real-world machine learning problem characterized by **extreme class imbalance**, **temporal patterns**, and **cost-sensitive decision making**.  
This project demonstrates an end-to-end ML workflow for detecting fraudulent transactions using simulated financial data.

---

## 📌 Project Overview

- **Problem Type:** Binary classification (Fraud vs Legitimate)
- **Domain:** Financial transactions
- **Challenge:** Fraud rate of only ~0.03%
- **Goal:** Identify suspicious transactions and assign fraud probability scores

---

## 📊 Dataset

- **Source:** Simulated transaction dataset
- **Format:** Daily `.pkl` files (April 2018)
- **Total Records:** 288,000+
- **Fraud Rate:** ~0.03%

### Key Columns
- `TRANSACTION_ID`
- `TX_DATETIME`
- `CUSTOMER_ID`
- `TERMINAL_ID`
- `TX_AMOUNT`
- `TX_FRAUD` (target variable)

---

## 🔧 Feature Engineering

### Temporal Features
Extracted from transaction timestamps:
- Hour of day
- Day of week
- Day of month
- Week of year
- Month and year

### Behavioral (Velocity) Features
- Total transaction count per customer
- Total transaction count per terminal  

These features help capture abnormal transaction frequency patterns.

---

## 🧠 Modeling Approach

### Models Trained

**Logistic Regression**
- Baseline model
- Trained with and without `class_weight='balanced'`

**Random Forest Classifier**
- 100 trees
- `class_weight='balanced'`
- Used for probability-based fraud scoring

### Preprocessing Pipeline
- Numerical features scaled using `StandardScaler`
- Categorical features encoded using `OneHotEncoder`
- Unified pipeline using `ColumnTransformer`

---

## ⚖️ Handling Class Imbalance

- Stratified train-test split (80/20)
- Class weights applied to penalize misclassification of fraud cases
- Evaluation focused on **recall, precision, and ROC-AUC**, not accuracy

---

## 📈 Evaluation & Results

### Key Observations
- Accuracy is misleading due to extreme class imbalance
- Models achieve high accuracy by correctly classifying legitimate transactions
- Fraud recall remains low due to very limited fraud samples in the test set
- Random Forest assigns non-zero fraud probability scores, enabling threshold-based risk control

### Metrics Used
- Confusion Matrix
- Precision & Recall
- ROC-AUC
- Predicted fraud probabilities

---

## 🔍 Threshold & Risk Analysis

- Fraud probabilities analyzed instead of hard labels
- Custom thresholds (e.g., 0.1) tested to study recall–precision trade-offs
- High-amount transactions (`TX_AMOUNT > 220`) analyzed as a known risk rule
- Demonstrates how ML models can support rule-based fraud detection systems

---

## 🛠️ Tech Stack

| Tool | Purpose |
|-----|--------|
| Python | Programming |
| Pandas / NumPy | Data processing |
| Scikit-learn | Modeling & pipelines |
| Matplotlib / Seaborn | Visualization |
| Jupyter Notebook | Experimentation |

---

## 🚀 How to Run

```bash
git clone https://github.com/SyedHussain23/fraud-transaction-detection.git
cd fraud-transaction-detection
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook fraud_detection.ipynb

---

## 🔮 Future Improvements
- Time-windowed velocity features
- SMOTE or cost-sensitive learning
- Gradient Boosting / XGBoost comparison
- Feature importance analysis
- Real-time fraud scoring API

---

## 👨‍💻 Author

**Syed Hussain Abdul Hakeem**

- LinkedIn: https://www.linkedin.com/in/syed-hussain-abdul-hakeem
- GitHub: https://github.com/SyedHussain23

---

## 📄 License

This project is open source and available under the MIT License.

---

## ⭐ Show Your Support

Give a ⭐️ if this project helped you!
