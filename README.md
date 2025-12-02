# Healthcare Provider Fraud Detection

![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=flat&logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat&logo=scikit-learn&logoColor=white)

A comprehensive machine learning solution for detecting healthcare provider fraud using claims data analysis and advanced feature engineering.

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Team Members](#team-members)
- [Key Results](#key-results)
- [Repository Structure](#repository-structure)
- [Dataset Description](#dataset-description)
- [Installation & Setup](#installation--setup)
- [How to Run](#how-to-run)
- [Methodology](#methodology)
- [Results](#results)
- [Deployment](#deployment)
- [Future Improvements](#future-improvements)

## 🎯 Project Overview

Healthcare fraud is a significant problem costing billions annually. This project develops a machine learning system to identify potentially fraudulent healthcare providers by analyzing their billing patterns, beneficiary demographics, and claim characteristics.

**Key Objectives:**
- Detect fraudulent healthcare providers with high precision
- Minimize false positives to avoid disrupting legitimate providers
- Provide interpretable results for regulatory review
- Handle severe class imbalance (9.4% fraud rate)

## 👥 Team Members

- **Data Scientist**: Advanced feature engineering and model development
- **ML Engineer**: Model optimization and deployment pipeline
- **Domain Expert**: Healthcare fraud pattern analysis
- **Project Lead**: Overall coordination and business alignment

## 🏆 Key Results

### Best Performing Model: **Random Forest**
- **F1-Score**: 0.8547
- **Precision**: 0.8125
- **Recall**: 0.9010
- **PR-AUC**: 0.8924

### Business Impact:
- **Fraud Detection Rate**: 90.1% of fraud cases identified
- **Precision Rate**: 81.3% of flagged cases are actual fraud
- **Cost Savings**: Significant reduction in investigation costs
- **Risk Mitigation**: Early detection prevents larger financial losses

### Technical Achievements:
- **Feature Engineering**: 27 comprehensive provider-level features
- **Data Processing**: 558,211 claims from 5,410 providers
- **Class Imbalance Handling**: Effective class weighting strategy
- **Model Comparison**: Evaluated 5 different algorithms

## 📁 Repository Structure

```
DataOrbit-HealthCare-Provider-Fraud-Detection/
├── README.md                           # Project documentation
├── data/                              # Data storage and outputs
│   ├── provider_level.csv             # Processed dataset for modeling
│   ├── model_results.csv              # Model comparison results
│   ├── feature_names.txt              # Feature reference
│   └── best_fraud_detection_model.pkl # Trained model (after running notebooks)
├── notebooks/                         # Jupyter notebooks
│   ├── 01_data_exploration_and_feature_engineering.ipynb
│   └── 02_modeling.ipynb
├── Train_Beneficiarydata-1542865627584.csv      # Beneficiary demographics
├── Train_Inpatientdata-1542865627584.csv        # Inpatient claims
├── Train_Outpatientdata-1542865627584.csv       # Outpatient claims
└── Train-1542865627584.csv                      # Provider fraud labels
```

## 📊 Dataset Description

### Source Data Files:
1. **Beneficiary Data** (138,556 records): Patient demographics, chronic conditions, coverage information
2. **Inpatient Claims** (40,474 records): Hospital stay claims with diagnosis/procedure codes
3. **Outpatient Claims** (517,737 records): Outpatient service claims and procedures
4. **Provider Labels** (5,410 records): Fraud/Non-fraud classifications

### Engineered Features (27 total):
- **Financial Features**: Total/average reimbursements, deductibles
- **Volume Features**: Claims counts, beneficiary counts, ratios
- **Network Features**: Physician diversity and relationships  
- **Medical Features**: Diagnosis and procedure diversity
- **Demographics**: Aggregated beneficiary characteristics

## 🛠 Installation & Setup

### Prerequisites:
```bash
# Python 3.8+
# Jupyter Notebook or JupyterLab
```

### Required Libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
```

### Alternative - Using conda:
```bash
conda install pandas numpy matplotlib seaborn scikit-learn
conda install -c conda-forge xgboost imbalanced-learn
```

## 🚀 How to Run

### Option 1: Complete Analysis (Recommended)
```bash
# 1. Clone/Download the repository
# 2. Ensure all CSV files are in the root directory
# 3. Open Jupyter Notebook/Lab
# 4. Run notebooks in sequence:

jupyter notebook notebooks/01_data_exploration_and_feature_engineering.ipynb
# Then run:
jupyter notebook notebooks/02_modeling.ipynb
```

### Option 2: Quick Start (Pre-processed Data)
```bash
# If you have the processed data file:
jupyter notebook notebooks/02_modeling.ipynb
```

### Expected Runtime:
- **Data Exploration & Feature Engineering**: ~15-20 minutes
- **Model Training & Evaluation**: ~5-10 minutes
- **Total Runtime**: ~25-30 minutes

## 🔬 Methodology

### 1. Data Exploration & Quality Assessment
- Comprehensive data quality analysis
- Missing value assessment and handling
- Target distribution analysis (class imbalance identification)

### 2. Feature Engineering
- **Provider-Level Aggregation**: Transform claim-level data to provider-level
- **Financial Patterns**: Reimbursement amounts, deductibles, claim volumes
- **Network Analysis**: Physician relationships and diversity
- **Medical Complexity**: Diagnosis and procedure code diversity
- **Beneficiary Demographics**: Patient population characteristics

### 3. Exploratory Data Analysis
- Feature correlation analysis
- Fraud vs. non-fraud pattern identification
- Statistical significance testing
- Visualization of key relationships

### 4. Model Development
- **Algorithms Tested**: Logistic Regression, Random Forest, Decision Tree, SVM, XGBoost
- **Class Imbalance Handling**: Balanced class weights (preferred over SMOTE)
- **Evaluation Strategy**: Stratified 5-fold cross-validation
- **Metrics Focus**: F1-score, Precision-Recall AUC for imbalanced data

### 5. Model Evaluation & Selection
- Comprehensive performance comparison
- Business impact assessment
- Model interpretability analysis
- Deployment readiness evaluation

## 📈 Results

### Model Performance Comparison:
| Model | Precision | Recall | F1-Score | PR-AUC |
|-------|-----------|--------|----------|---------|
| **Random Forest** | **0.8125** | **0.9010** | **0.8547** | **0.8924** |
| XGBoost | 0.7838 | 0.8911 | 0.8341 | 0.8756 |
| Logistic Regression | 0.7500 | 0.8812 | 0.8103 | 0.8445 |
| Decision Tree | 0.7297 | 0.8713 | 0.7944 | 0.8123 |
| SVM | 0.7143 | 0.8515 | 0.7774 | 0.8034 |

### Key Insights:
1. **Random Forest** emerged as the best performer with optimal precision-recall balance
2. **Class weighting** proved more effective than synthetic data generation (SMOTE)
3. **Feature importance** analysis revealed financial patterns as strongest fraud indicators
4. **Provider network characteristics** showed significant predictive power

### Feature Importance (Top 10):
1. InscClaimAmtReimbursed_sum
2. TotalClaims
3. UniqueBeneficiaries
4. InscClaimAmtReimbursed_mean
5. ClaimsPerBeneficiary
6. TotalUniquePhysicians
7. UniqueDiagnoses
8. AvgBeneIPReimbursement
9. InpatientRatio
10. UniqueProcedures

## 🚀 Deployment

### Recommended Deployment Strategy:

1. **Model Export**: Best model saved as `best_fraud_detection_model.pkl`
2. **API Integration**: RESTful API for real-time scoring
3. **Batch Processing**: Weekly/monthly batch analysis of new providers
4. **Monitoring**: Performance drift detection and retraining alerts

### Production Considerations:
- **Threshold Tuning**: Adjust based on investigation capacity and cost considerations
- **Explainability**: Feature importance and SHAP values for audit trails
- **Retraining**: Quarterly model updates with new fraud patterns
- **Data Pipeline**: Automated feature engineering for new claims data

## 🔮 Future Improvements

### Technical Enhancements:
1. **Time-Series Features**: Seasonal fraud patterns and temporal dependencies
2. **Network Analysis**: Advanced graph-based features for provider relationships
3. **Deep Learning**: Neural networks for complex pattern recognition
4. **Ensemble Methods**: Stacking multiple algorithms for improved performance

### Data Enhancements:
1. **External Data**: Provider licensing, regulatory actions, geographic factors
2. **Real-time Features**: Streaming analytics for immediate detection
3. **Unstructured Data**: Text mining of claim notes and descriptions
4. **Synthetic Features**: Advanced feature engineering with domain expertise

### Business Integration:
1. **Risk Scoring**: Multi-tier risk classification system
2. **Investigation Workflow**: Automated case prioritization and routing
3. **Regulatory Compliance**: Integration with healthcare fraud reporting systems
4. **Cost-Benefit Analysis**: ROI measurement and optimization

---

## 📝 License

This project is developed for educational and research purposes. Please ensure compliance with healthcare data privacy regulations when using similar datasets.

## 🤝 Contributing

We welcome contributions! Please read our contributing guidelines and submit pull requests for any improvements.

## 📞 Contact

For questions, suggestions, or collaboration opportunities, please reach out to the project team.

---

**Note**: This project demonstrates advanced machine learning techniques for fraud detection while maintaining focus on interpretability and business value. The methodologies can be adapted for other fraud detection domains with appropriate modifications.
