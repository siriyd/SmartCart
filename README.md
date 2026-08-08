# SmartCart Customer Segmentation System

SmartCart is an unsupervised machine learning project developed to segment retail customers based on their demographics, income, purchasing behavior, household characteristics, and product spending patterns.

The objective is to identify meaningful customer groups that can support targeted marketing, personalized promotions, loyalty programs, and customer retention strategies.

## Project Overview

The dataset contains 2,240 customer records with attributes such as:

- Income
- Age
- Education
- Marital status
- Number of children
- Customer tenure
- Recency
- Product-category spending
- Web, catalog, and store purchases
- Deal purchases
- Campaign response

The project follows an end-to-end customer segmentation workflow involving data cleaning, feature engineering, dimensionality reduction, clustering, cluster validation, and business interpretation. :contentReference[oaicite:0]{index=0}

## Machine Learning Workflow

### 1. Data Preprocessing

- Inspected feature types, dataset dimensions, and missing values.
- Filled missing income values using median imputation.
- Removed implausible age values and one extreme income observation.
- Excluded identifiers and redundant raw attributes before clustering.

### 2. Feature Engineering

Created customer-focused features including:

- `Age` from year of birth
- `Customer_Tenure_Days` from enrollment date
- `Total_Children` by combining children and teenagers at home
- `Living_With` by grouping marital status into partner and alone categories
- Broader education groups such as undergraduate, graduate, and postgraduate

### 3. Spending Feature Reduction

The dataset contained six product-spending attributes:

- Wine
- Fruits
- Meat
- Fish
- Sweets
- Gold products

These features were standardized and reduced using Principal Component Analysis.

The first two spending components explained approximately:

- PC1: 56.1%
- PC2: 12.3%

Together, they retained about 68.4% of the standardized spending-pattern variance. :contentReference[oaicite:1]{index=1}

### 4. Feature Encoding and Scaling

- Applied One-Hot Encoding to categorical features.
- Standardized the final feature set using `StandardScaler`.
- Applied PCA to obtain a lower-dimensional representation for cluster visualization and modeling.

### 5. Selecting the Number of Clusters

The number of clusters was evaluated using:

- Elbow Method
- KneeLocator
- Silhouette Score

KneeLocator identified the elbow at:

```text
K = 4
```

Four clusters were selected to balance cluster quality, interpretability, and business usefulness. :contentReference[oaicite:2]{index=2}

### 6. Clustering Algorithms

Two unsupervised learning algorithms were applied:

- K-Means Clustering
- Agglomerative Hierarchical Clustering using Ward linkage

The final customer profiles were interpreted using the Agglomerative Clustering labels.

## Customer Segments

### Cluster 0 — High-Value Customers

- High income
- High overall spending
- Frequent catalog and store purchases
- Low sensitivity to discounts

**Recommended strategy:** Premium offers, exclusive memberships, and loyalty rewards.

### Cluster 1 — Price-Sensitive Individual Customers

- Low-to-moderate income
- Lower spending
- Predominantly living alone
- Relatively high website activity

**Recommended strategy:** Discount notifications, limited-time offers, and personalized digital campaigns.

### Cluster 2 — Budget-Conscious Family Customers

- Lower income and spending
- Predominantly living with partners
- Fewer catalog and store purchases
- Low campaign response

**Recommended strategy:** Value bundles, family-oriented promotions, and practical discounts.

### Cluster 3 — Engaged Premium Family Customers

- Moderate-to-high income
- Strong spending
- Frequent web and store purchases
- Predominantly living with partners

**Recommended strategy:** Cross-selling, loyalty campaigns, and premium family bundles.

Clusters 0 and 3 represent premium customer groups, while Clusters 1 and 2 are more price-sensitive. :contentReference[oaicite:3]{index=3}

## Key Observations

- Income showed a strong positive association with Spending PC1.
- Higher-income customers tended to make more catalog and store purchases.
- Income was negatively associated with monthly website visits.
- Spending PC1 was strongly associated with catalog and store purchasing activity. :contentReference[oaicite:4]{index=4}

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Kneed

## Repository Structure

```text
SmartCart-Customer-Segmentation/
│
├── SmartCart.ipynb
├── README.md
└── .gitignore
```

> The dataset is intentionally excluded from this repository.

## How to Run

1. Clone the repository.
2. Install the required Python libraries.
3. Place the dataset in the project directory.
4. Open the notebook in Jupyter Notebook or JupyterLab.
5. Run the cells sequentially to reproduce the preprocessing, clustering, and customer-segmentation results.

## Conclusion

This project demonstrates an end-to-end unsupervised machine learning workflow for retail customer segmentation.

By combining feature engineering, PCA, cluster validation, K-Means, and Agglomerative Clustering, the project identified four actionable customer groups that can support personalized marketing and customer relationship strategies.
