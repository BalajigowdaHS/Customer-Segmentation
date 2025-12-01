# Customer Segmentation Using Clustering

## Project Overview
Customer segmentation is a marketing technique that groups customers based on shared characteristics and behaviors so that businesses can tailor strategies for each segment. In this project, we analyze a marketing campaign dataset of 2,240 customers (29 features) to uncover distinct customer segments based on demographic attributes, purchasing patterns, and response to marketing campaigns.

## Dataset
The `marketing_campaign.csv` dataset contains 29 features, including:

- **Demographic features:** `Year_Birth`, `Education`, `Marital_Status`, `Income`.
- **Behavioral features:** amounts spent in product categories (`MntWines`, `MntFruits`, `MntMeatProducts`, etc.), purchase counts across channels (`NumWebPurchases`, `NumCatalogPurchases`, etc.), `Recency`, and acceptance of marketing campaigns (`AcceptedCmp1`–`AcceptedCmp5`, `Response`).
- **Customer registration:** `Dt_Customer` indicates when each customer joined.

These features provide a comprehensive view of customer demographics and purchasing behavior.

## Data Preprocessing
Key preprocessing steps included:

1. **Handling missing data:** Records with missing values were removed to maintain data integrity.
2. **Feature engineering:** Derived variables such as `Age` (based on `Year_Birth`), `Spent` (total amount spent across all product categories), `Children` (`KidHome` + `TeenHome`), `Family_Size`, `Customer_For` (number of days since joining), and `Living_With` (derived from marital status) to capture household context.
3. **Encoding categorical variables:** Converted categorical features like `Education` and `Marital_Status` to numeric codes using label encoding.
4. **Scaling:** Standardized numerical features to ensure equal influence during clustering.

## Dimensionality Reduction
To visualize high-dimensional data and improve clustering performance, we applied Principal Component Analysis (PCA) to reduce the dataset to three principal components while retaining most of the variance. The first two components were used for 2D visualization.

## Clustering Methodology
We experimented with KMeans and Agglomerative clustering. Using the Elbow Method on the PCA-transformed data, we found that **4 clusters** balance within-cluster compactness and between-cluster separation. Silhouette scores (~0.67 for KMeans and ~0.62 for Agglomerative) confirmed reasonable cluster quality.

## Insights
The four clusters reveal distinct customer profiles:

- **Cluster 1 (High‑value customers):** High income, high spending, longer tenure, and high response to campaigns.
- **Cluster 2 (Younger budget shoppers):** Moderate income, low spending, minimal engagement with campaigns.
- **Cluster 3 (Low‑income families):** Low income, low spending, often families with children, limited response to marketing.
- **Cluster 4 (Middle‑aged moderate spenders):** Medium income and moderate spending; mixed campaign responsiveness.

These segments provide actionable insights for targeted marketing—e.g., upselling and loyalty rewards for Cluster 1, and cost‑sensitive promotions for Clusters 2 and 3.

## Future Work
- Explore density‑based clustering algorithms (DBSCAN, Gaussian Mixture Models) for non‑spherical clusters.
- Tune clustering hyperparameters (initialization, number of iterations) to refine segments.
- Incorporate additional features (e.g., recency of purchases per category) to capture more behavior nuances.

## Repository Structure
- **Customer Segementation.ipynb** – Jupyter notebook with data cleaning, feature engineering, PCA, clustering, and visualization.
- **marketing_campaign.csv** – Raw dataset of customer attributes and campaign interactions.
- **README.md** – Project documentation (this file).

## Getting Started

1. Clone the repository:

```bash
git clone https://github.com/BalajigowdaHS/Customer-Segmentation.git
cd Customer-Segmentation
```

2. Install required packages:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

3. Run the notebook:

```bash
jupyter notebook "Customer Segementation.ipynb"
```

Explore the notebook to see detailed analysis and cluster visualizations.
