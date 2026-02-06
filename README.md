# 💳 Fraud Transaction Detection

Fraud detection is a high-impact, real-world ML problem involving extreme class imbalance, temporal patterns, and cost-sensitive errors.
This project demonstrates an end-to-end, production-style machine learning workflow using simulated transaction data from daily `.pkl` files (April 2018).

---

## 📁 Repository Files

- **`fraud_detection.ipynb`**: Complete end-to-end implementation including data loading, exploratory analysis, feature engineering, model training, and evaluation

---

## 📊 Dataset

### Overview
- **Format**: 30 separate `.pkl` files (one file per day of April 2018)
- **Total Records**: 288,000+ transactions after combining all daily files
- **Class Imbalance**: Fraudulent transactions represent only ~0.03% of total data

### Key Features
- `TRANSACTION_ID`: Unique transaction identifier
- `TX_DATETIME`: Transaction timestamp
- `CUSTOMER_ID`: Customer identifier
- `TERMINAL_ID`: Terminal/location identifier
- `TX_AMOUNT`: Transaction amount
- `TX_FRAUD`: Target variable (0 = legitimate, 1 = fraudulent)

---

## 🔧 Feature Engineering

### Temporal Features
Extracted from transaction timestamps:
- Hour of day, day of week, day of month
- Week of year, month, year

### Behavioral (Velocity) Features
- Rolling transaction count per customer (behavioral velocity)
- Rolling transaction count per terminal (location risk signal)

These velocity features help identify unusual transaction frequencies that may indicate fraud.

---

## 🧠 Machine Learning Model

### Model: Random Forest Classifier
- **Algorithm**: Ensemble learning with 100 decision trees
- **Class Balancing**: Applied `class_weight='balanced'` to handle extreme class imbalance
- **Pipeline**: Includes StandardScaler and OneHotEncoder for preprocessing

### Evaluation Metrics
- **Confusion Matrix**: Detailed breakdown of predictions vs actual values
- **Accuracy**: Overall correctness of predictions
- **Precision**: Accuracy of fraud predictions
- **Recall**: Ability to catch actual fraud cases
- **ROC-AUC Score**: Model's discrimination ability

### Output
Each transaction receives a `predicted_fraud_probability` score (0-1) indicating likelihood of fraud.

---

## 🛠️ Setup & Requirements

### Prerequisites
```bash
Python 3.8+
Jupyter Notebook
```

### Installation
```bash
# Clone the repository
git clone https://github.com/SyedHussain23/fraud-transaction-detection.git
cd fraud-transaction-detection

# Install required packages
pip install pandas numpy scikit-learn matplotlib jupyter
```

### Required Libraries
- **pandas**: Data manipulation
- **scikit-learn**: Machine learning algorithms
- **matplotlib & seaborn**: Data visualization
- **zipfile & os**: File handling

---

## 🚀 Usage

1. Place your `dataset.zip` (containing 30 .pkl files) in the project root
2. Open Jupyter Notebook:
   ```bash
   jupyter notebook fraud_detection.ipynb
   ```
3. Run all cells to execute the complete pipeline

---

## 📈 Project Workflow

1. **Data Loading**: Extract and combine 30 daily `.pkl` files from `dataset.zip`
2. **Exploratory Analysis**: Check for missing values, data types, and class distribution
3. **Feature Engineering**: Create temporal and behavioral features
4. **Preprocessing**: Scale numerical features and encode categorical variables
5. **Model Training**: Train Random Forest Classifier with balanced class weights
6. **Evaluation**: Generate predictions and assess performance using multiple metrics

---

## 💻 Technologies Used

| Technology | Purpose |
|------------|---------|
| Python 3.8+ | Programming language |
| Pandas | Data manipulation |
| Scikit-learn | Machine learning |
| Matplotlib/Seaborn | Visualization |
| Jupyter Notebook | Development environment |

---

## 🔮 Future Improvements

- [ ] Implement SMOTE for better class balance handling
- [ ] Add XGBoost and compare performance
- [ ] Create real-time fraud detection API
- [ ] Develop interactive dashboard
- [ ] Add feature importance analysis

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

---
