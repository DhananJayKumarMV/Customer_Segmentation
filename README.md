# Customer Segmentation

Unsupervised segmentation of an online retail customer base, combining transaction history, demographics, and behavioral data to group customers into actionable segments.

## Data

Three source tables (in `data/`), joined on `Customer_ID`:
- **Customer demographics** — age, gender, location, etc.
- **Customer invoices** — transaction-level purchase history (item, quantity, price, date).
- **Customer behaviour** — engagement/behavioral signals.

## Approach

1. **Cleaning** — missing-value treatment and duplicate removal on each source table independently, then merge on `Customer_ID`.
2. **EDA** — revenue trends by invoice year/month/week/quarter, revenue and order volume by country, most frequent product descriptions and stock codes (see the charts in this repo).
3. **Clustering** — K-Means over a range of cluster counts (3–9), selecting `k=5` by silhouette score (tuned to ≥ 0.145); also compared against a Gaussian Mixture Model.
4. **Evaluation** — silhouette plots and an elbow curve to validate cluster separation and choice of `k`.

## Notebooks

| Notebook | Purpose |
|---|---|
| `Customer_Segmentation.ipynb` | Main pipeline — cleaning, merging, EDA, clustering, evaluation. Start here. |
| `Customer_demographics.ipynb` | Demographics-only cleaning and EDA. |
| `Invoice Data Cleaning.ipynb` | Invoice-table cleaning in isolation. |
| `Customer_behaviour.ipynb` | Behavioral-data exploration. |
| `Miniproject_USML.ipynb` | Earlier/coursework version of the main pipeline. |
| `online_customer-segmentation-recommendation-system.ipynb` | Reference notebook adapted from [Farzad Nekouee's Retail Customer Segmentation & Recommendation System](https://github.com/FarzadNekouee/Retail_Customer_Segmentation_Recommendation_System), kept for comparison — not original work. |

## Results

- Cluster and silhouette plots: `Cluster results.png`, `Silhouette Plot.png`, `Elbow curve.png`, `Kmeans_clustering_picture.png`, `gmm_clustering_picture.png`
- EDA visualizations: `Correlation Matrix.png`, `Distribution_of_order_amounts.png`, `Top 30 Most Frequent Descriptions.png`, `top_10_countries_generating_revenue.png`, `top_10_stock_codes.png`

## Stack

Python · pandas · scikit-learn (K-Means, Gaussian Mixture, silhouette score) · Jupyter
