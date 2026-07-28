# Assignment7-for-IN26011064


## 🛍️ Customer Segmentation using K-Means Clustering and PCA

> Unsupervised machine learning project to segment mall customers into distinct groups based on their annual income and spending behaviour, enabling targeted marketing strategies.

**Author:** Kushagra Raghuvanshi  

**Registration Number:** 23BSA10072

**Application Number:** IN26011064

**Batch Number:** 2B

**Email ID:** kushagra.23bsa10072@vitbhopal.ac.in

---

## 📌 Objective

The goal of this project is to:

- Apply **K-Means Clustering** to group mall customers into meaningful segments based on their demographic and behavioural attributes.
- Use the **Elbow Method** to identify the optimal number of clusters.
- Apply **Principal Component Analysis (PCA)** to reduce dimensionality and visualize the clusters in 2D space.
- Derive actionable business insights from the identified customer segments to support targeted marketing campaigns.

---

## 📊 Dataset

**Mall Customer Segmentation Dataset**

| Detail | Info |
|--------|------|
| Source | Kaggle |
| Link | [https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python) |
| Records | 200 customers |
| Features | 5 (CustomerID, Gender, Age, Annual Income, Spending Score) |

### Feature Description

| Column | Type | Description |
|--------|------|-------------|
| `CustomerID` | Integer | Unique identifier (dropped during preprocessing) |
| `Gender` | Categorical | Male / Female |
| `Age` | Integer | Age of the customer (years) |
| `Annual Income (k$)` | Integer | Annual income in thousands of dollars |
| `Spending Score (1–100)` | Integer | Score assigned by the mall based on spending behaviour |

---

## 📦 Libraries Used

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥ 1.5 | Data loading, manipulation, and exploration |
| `numpy` | ≥ 1.23 | Numerical computations |
| `matplotlib` | ≥ 3.6 | Plotting graphs and visualizations |
| `seaborn` | ≥ 0.12 | Enhanced statistical visualizations |
| `scikit-learn` | ≥ 1.2 | KMeans clustering, PCA, StandardScaler, LabelEncoder |

## 🔬 Methodology

### Step 1 — Data Understanding
- Loaded the dataset using `pandas.read_csv()`.
- Inspected the first 5 records, feature data types, and summary statistics.
- Identified **4 numerical features** and **1 categorical feature** (Gender).

### Step 2 — Data Preprocessing
- Checked for missing values → **None found**.
- Dropped `CustomerID` as it is an identifier with no predictive value.
- Applied **Label Encoding** to the `Gender` column (Female = 0, Male = 1).
- Standardized all features using **StandardScaler** (mean = 0, std = 1) to ensure equal feature contribution to clustering.

### Step 3 — Model Development

**Elbow Method:**
Ran K-Means for K = 1 to 10 and plotted the Within-Cluster Sum of Squares (WCSS / Inertia). The curve showed a clear "elbow" at **K = 5**, indicating the optimal number of clusters.

**K-Means Clustering:**
Trained a `KMeans` model with `n_clusters=5`, `random_state=42`, and `n_init=10`. Cluster labels were assigned to each customer record.

**PCA:**
Applied `PCA(n_components=2)` to reduce the 4-dimensional scaled feature space to 2 principal components for 2D visualization.

### Step 4 — Visualization & Evaluation
Generated three key plots:
1. **Elbow Curve** — to determine optimal K.
2. **Cluster Scatter Plot** — Annual Income vs Spending Score, coloured by cluster with centroids marked.
3. **PCA 2D Plot** — clusters visualized in principal component space, plus an explained variance bar chart.

---

## 📈 Results

### Elbow Method
The WCSS drops sharply from K = 1 to K = 5 and flattens thereafter. **K = 5** is the optimal number of clusters.

### PCA Explained Variance

| Component | Individual Variance | Cumulative Variance |
|-----------|-------------------|-------------------|
| PC1 | 35.44% | 35.44% |
| PC2 | 24.86% | 60.30% |

Two principal components together capture **~60.3%** of total dataset variance.

### Cluster Profiles

| Cluster | Avg Income (k$) | Avg Spending Score | Customer Type |
|---------|----------------|-------------------|---------------|
| 0 | ~55 | ~45 | Mid Income / Low Spend — Conservative spenders |
| 1 | ~26 | ~20 | Low Income / Low Spend — Budget-conscious customers |
| 2 | ~87 | ~82 | High Income / High Spend — Premium customers ⭐ |
| 3 | ~55 | ~55 | Mid Income / Mid Spend — Average / Balanced customers |
| 4 | ~26 | ~78 | Low Income / High Spend — Aspirational / Impulsive buyers |

### Key Observations
1. The elbow at K = 5 confirms five distinct and meaningful customer segments exist in the data.
2. PCA successfully compressed 4 features into 2 dimensions while retaining 60.3% of total information, enabling clear 2D visualization of the clusters.
3. Cluster 2 (High Income / High Spend) represents the mall's most valuable customer segment for premium marketing.
4. Cluster 4 (Low Income / High Spend) is a high-priority segment for EMI, instalment, or loyalty-reward campaigns.

---

## ✅ Conclusion

This project successfully demonstrated how unsupervised machine learning can uncover hidden patterns in customer data without labelled data. K-Means clustering with K = 5 identified five behaviorally distinct customer groups, and PCA provided an intuitive 2D view of these segments despite the multi-dimensional feature space.

**Business applications** include personalized marketing campaigns, product recommendations, and loyalty programme design tailored to each segment's income and spending profile — directly improving the mall's marketing ROI.

**Limitation of K-Means:** Requires the number of clusters to be pre-defined and assumes clusters are spherical and of similar size, which may not always hold in real customer data.

**Advantage of PCA:** Reduces high-dimensional data to fewer components while preserving maximum variance, aiding both visualization and computational efficiency in downstream models.

---

*Assignment | Customer Segmentation using K-Means Clustering and PCA*
