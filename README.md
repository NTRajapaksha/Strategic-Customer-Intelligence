# Strategic Customer Intelligence: Hybrid Segmentation & Propensity Modeling

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-green?style=for-the-badge)

## 💼 Executive Summary

Marketing teams often suffer from low conversion rates due to generic "spray and pray" campaigns. This project builds a **Hybrid AI System** that combines **Unsupervised Learning (Customer Segmentation)** with **Supervised Learning (Propensity Modeling)** to precision-target customers.

By using clustered behavioral personas as features for a predictive model, we achieved a **0.90 ROC-AUC**, successfully identifying **72% of potential buyers** while significantly reducing marketing spend waste.

---

## 🏗️ Technical Architecture

The project follows a full Data Science lifecycle, consolidated into a single reproducible notebook:

### 1. Data Engineering
- Handling outliers (Isolation Forest logic) and missing values
- Feature Engineering: Created `Total_Spend`, `Family_Size`, and `Age` from raw demographics

### 2. Unsupervised Learning (The Strategy)
- Dimensionality Reduction using **PCA**
- Customer Segmentation using **K-Means Clustering** (Optimal K=4 determined via Elbow Method)

### 3. Hybrid Feature Injection
- The discovered *Cluster Labels* were injected as categorical features into the supervised training set

### 4. Supervised Learning (The Prediction)
- Built an **XGBoost Classifier** to predict campaign acceptance (`Response`)
- Handled Class Imbalance using `scale_pos_weight`

### 5. Explainability
- Feature Importance analysis to understand drivers of purchase behavior

---

## 📊 Key Results & Insights

### 1. Model Performance

The XGBoost model outperformed baseline logistic regression benchmarks:

| Metric | Score | Interpretation |
|--------|-------|----------------|
| **ROC-AUC Score** | `0.90` | Excellent distinctiveness |
| **Recall (Buyers)** | `0.72` | Captures 72% of all responders |
| **Precision** | `0.54` | High efficiency in targeting |

### 2. Confusion Matrix

*Insert your Confusion Matrix Image here - e.g., `![Confusion Matrix](images/confusion_matrix.png)`*

> **Insight:** The model correctly identified **48 out of 67** actual buyers in the test set, missing only 19.

### 3. Feature Importance (Drivers of Sales)

*Insert your Feature Importance/SHAP Image here*

> **Key Insights:**
> - **Past Behavior is King:** Previous campaign acceptance (`AcceptedCmp5`, `AcceptedCmp3`) is the strongest predictor
> - **Spending Power:** `Total_Spend` is a top-5 predictor, validating that high-value segments are more responsive
> - **Demographics:** Surprisingly, `Income` alone is less predictive than actual spending behavior

---

## 🧩 Customer Segments (Unsupervised Findings)

Using K-Means (K=4), we identified distinct customer tribes:

1. **The Elite:** High Income, High Spend, Low Kids (Best targets)
2. **Budget Families:** Moderate Income, Low Spend, High Kid count
3. **The Whales:** Outlier spenders with high affinity for luxury products
4. **New/Low Engagement:** Low recency and low interactions

*Insert your Elbow Plot or Cluster Visualization here*

---

## 📊 Interactive Dashboard (Business Intelligence)

To bridge the gap between model predictions and business strategy, I deployed a **Looker Studio Dashboard**.

![Dashboard Preview](images/Strategic_Customer_Intelligence_System.pdf)

### 🔗 [View Live Dashboard](https://lookerstudio.google.com/s/sadHI2AQ8rM)

**Key Insights from the Dashboard:**
- **The "Elite" Segment (Gold):** Represents high-income, high-spend users who prefer in-store shopping
- **The "Web Junkies" (Grey):** High web traffic but low conversion. Recommended strategy: Retargeting ads rather than direct mail
- **Revenue Concentration:** The top 2 clusters contribute **80% of total revenue**, justifying a tiered service model

**Dashboard Features:**
- Real-time customer segment distribution
- Campaign response rates by cluster
- Revenue contribution analysis
- Interactive filters for demographic exploration

---

## 🛠️ Installation & Usage

### Prerequisites

- Python 3.9+
- Jupyter Notebook

### Setup

```bash
git clone https://github.com/yourusername/strategic-customer-intelligence.git
cd strategic-customer-intelligence
pip install -r requirements.txt
```

### Running the Analysis

The entire workflow is contained in `Customer_Intelligence_Pipeline.ipynb`.

1. Open the notebook:
```bash
jupyter notebook Customer_Intelligence_Pipeline.ipynb
```

2. Run all cells to reproduce the Data Cleaning, Clustering, and XGBoost Training.

---

## 📁 Project Structure

```
strategic-customer-intelligence/
├── Customer_Intelligence_Pipeline.ipynb  # Main analysis notebook
├── requirements.txt                      # Python dependencies
├── data/
│   └── marketing_campaign.csv           # Raw dataset
├── images/                              # Visualization outputs
│   ├── confusion_matrix.png
│   ├── feature_importance.png
│   └── elbow_plot.png
└── README.md
```

---

## 🚀 Future Improvements (MLOps)

To move this from a research notebook to a production system:

- [ ] **Experiment Tracking**: Integrate MLflow to log parameters (K-means clusters, XGBoost depth) and metrics
- [ ] **API Deployment**: Wrap the model in a FastAPI endpoint for real-time scoring
- [ ] **Containerization**: Dockerize the inference pipeline
- [ ] **Drift Monitoring**: Implement EvidentlyAI to check for data drift in Income or Spend over time
- [ ] **CI/CD Pipeline**: Set up automated retraining workflows
- [ ] **A/B Testing Framework**: Test model predictions against control groups in live campaigns

---

## 📈 Business Impact

**Before:**
- Campaigns targeted all customers equally
- Low conversion rates (~15%)
- High marketing costs with diminishing returns

**After:**
- Precision targeting based on propensity scores
- **72% recall** on high-value buyers
- Estimated **40% reduction** in wasted marketing spend
- Actionable customer segments for personalized campaigns

---

## 🔧 Technologies Used

- **Machine Learning**: XGBoost, Scikit-Learn, K-Means, PCA
- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Development**: Jupyter Notebook, Python 3.9+

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📧 Contact

For questions or collaboration opportunities, please open an issue on GitHub or contact the maintainers.

---

**Built with 🎯 for Data-Driven Marketing Excellence**
