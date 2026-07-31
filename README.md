# Customer Segmentation for a Retail Banking Dataset

## Overview

This project presents a leakage-free customer segmentation framework for a retail banking dataset containing **30,000 customer records** and **29 customer-related attributes**. The objective is to identify meaningful customer segments that can support targeted marketing, customer retention, and business decision-making while preventing information leakage.

Unlike the initial workflow, outcome variables (`churn_prob`, `churn_flag`, and `risk_score`) were excluded from clustering and used only for post-clustering validation. This ensures that the discovered customer segments are statistically valid and suitable for real-world business applications.

---

## Objectives

- Segment retail banking customers using K-Means clustering.
- Prevent data leakage by excluding outcome variables from clustering.
- Determine the optimal number of clusters using multiple cluster validation metrics.
- Profile each customer segment using demographic, financial, and behavioural characteristics.
- Validate discovered segments using churn probability, churn rate, and risk score.
- Perform additional analyses to evaluate the robustness and business relevance of the segmentation.

---

## Dataset

The dataset contains **30,000 customer records** with demographic, financial, behavioural, and engagement-related features.

Some important variables include:

- Age
- Gender
- Marital Status
- City Tier
- Annual Income
- Credit Score
- Savings Rate
- Loan Amount
- Product Count
- Transaction Count
- Mobile App Logins
- Branch Visits
- Debt-to-Income Ratio
- Engagement Score

Outcome variables:

- risk_score
- churn_prob
- churn_flag

These outcome variables are **excluded during clustering** and are used only for validation.

---

## Methodology

The workflow consists of the following steps:

1. Remove `customer_id`.
2. Exclude outcome variables to prevent information leakage.
3. One-hot encode categorical variables.
4. Standardize numerical features using StandardScaler.
5. Apply K-Means clustering for values of **k = 2 to 10**.
6. Evaluate cluster quality using:
   - Inertia (Elbow Method)
   - Silhouette Score
   - Calinski-Harabasz Index
   - Davies-Bouldin Index
7. Select the optimal number of clusters.
8. Profile each cluster using feature averages.
9. Validate clusters using churn and risk-related variables.
10. Visualize clusters using PCA and financial feature plots.

---

## Cluster Evaluation Metrics

The following metrics were used:

- Elbow Method (Inertia)
- Silhouette Score
- Calinski-Harabasz Index
- Davies-Bouldin Index

The Silhouette Score was selected as the primary criterion because it balances cluster cohesion and separation while remaining easier to interpret than inertia alone.

---

## Results

### Optimal Number of Clusters

- **k = 4**

### Final Model Performance

| Metric | Value |
|---------|--------|
| Silhouette Score | 0.0752 |
| Calinski-Harabasz Score | 1561.03 |
| Davies-Bouldin Score | 2.800 |

---

## Cluster Summary

### Cluster 0

- Small customer group
- Mostly widowed customers
- Normal financial behaviour
- Low churn

### Cluster 1

- High loan amount
- High debt-to-income ratio
- Highest churn rate (51.9%)
- Highest risk score
- Represents approximately **7.4%** of customers
- Primary target for retention strategies

### Cluster 2

- Mostly single customers
- Moderate financial behaviour
- Low churn

### Cluster 3

- Mostly married customers
- Financial characteristics similar to Cluster 2
- Low churn

---

## Additional Analyses

The notebook extends the basic clustering workflow by including:

- Marital status relevance analysis
- ANOVA feature importance
- Alternative distance metrics
- Numeric-only clustering
- Hierarchical clustering comparison
- Risk score prediction using regression
- Self-Organizing Map (SOM)
- Decision Tree validation of Cluster 1
- Supervised Retain vs Do Not Encourage classification
- Re-clustering without marital status variables

---

## Key Findings

- Outcome leakage significantly changes clustering behaviour.
- Removing outcome variables changed the optimal solution from **k = 2** to **k = 4**.
- A small customer segment with very high debt and loan exposure exhibits approximately **three times higher churn** than the remaining customer base.
- Marital status strongly influences Euclidean K-Means because of one-hot encoding.
- Behaviour-first clustering would benefit from mixed-data methods such as Gower distance or K-Prototypes.

---

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- SciPy
- Matplotlib
- Seaborn

---

## Repository Structure

```
Customer-Segmentation/
│
├── Customer_Segmentation_TIH(2).ipynb
├── Customer Segmentation Report.pdf
├── README.md
└── dataset.csv
```

---

## How to Run

1. Clone the repository.
2. Install the required Python packages.
3. Open the Jupyter Notebook.
4. Update the dataset path if necessary.
5. Run the notebook sequentially from top to bottom.
6. Review the generated evaluation metrics, cluster profiles, visualizations, and validation analyses.

---

## Business Recommendations

- Prioritize **Cluster 1** for customer retention campaigns.
- Offer debt restructuring and personalized financial support to high-risk customers.
- Use the remaining clusters for relationship management and targeted product recommendations.
- Consider replacing Euclidean K-Means with mixed-data clustering techniques in future work.

---

## Future Work

- Implement K-Prototypes clustering.
- Apply Gower distance for mixed-type data.
- Compare clustering with DBSCAN and Gaussian Mixture Models.
- Develop a production-ready customer retention prediction pipeline.
- Deploy the solution as an interactive dashboard.

---

## References

- MacQueen (1967) – K-Means Clustering
- Lloyd (1982) – Least Squares Quantization
- Rousseeuw (1987) – Silhouette Score
- Calinski & Harabasz (1974)
- Davies & Bouldin (1979)
- Gower (1971)
- Breiman et al. (1984) – CART
- Kohonen (1990) – Self-Organizing Map
- Pedregosa et al. (2011) – Scikit-learn
- Han, Kamber & Pei (2011) – Data Mining: Concepts and Techniques

---

## Author

**Megha R**  
Student, MSc Artificial Intelligence & Machine Learning  
Jamia Millia Islamia, New Delhi

**Project Guide:**  
Prof. Dipti Prasad Mukherjee

**Internship Organization:**  
IDEAS Foundation, Indian Statistical Institute (ISI), Kolkata
