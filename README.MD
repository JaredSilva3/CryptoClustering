# Module 19 Unsupervised Machine Learning Report

## Overview of the Analysis

The goal of this analysis was to use unsupervised machine learning techniques to group cryptocurrencies into clusters based on their price changes over 24 hours and 7 days. The analysis was performed using K-Means clustering with and without Principal Component Analysis (PCA) to evaluate the impact of dimensionality reduction on the clustering results.

### Data Information:
- **Dataset**: `crypto_market_data.csv` containing cryptocurrency performance metrics.
- **Features**:
  - `price_change_percentage_24h`: Price change percentage over 24 hours.
  - `price_change_percentage_7d`: Price change percentage over 7 days.
- **Index**: `coin_id`, representing the names of the cryptocurrencies.

---

## Machine Learning Process

This analysis was divided into the following stages:

### 1. **Data Preparation**
   - The dataset was loaded and scaled using the `StandardScaler` from `scikit-learn` to normalize the features.
   - A new scaled DataFrame was created with `coin_id` set as the index.

### 2. **Find the Optimal Value of k (Elbow Method)**
   - The Elbow Method was used to determine the best value for `k` (number of clusters) by plotting the inertia values for `k` ranging from 1 to 11.
   - This was performed on both:
     - The **original scaled data**.
     - The **PCA-transformed data**.

### 3. **Cluster Cryptocurrencies**
   - K-Means clustering was applied:
     - First using the **original scaled data**.
     - Then using the **PCA-transformed data** with `n_components=3` to reduce the dimensions to three principal components.
   - The clusters were visualized using scatter plots:
     - **Original Data**: Plotted with `price_change_percentage_24h` and `price_change_percentage_7d`.
     - **PCA Data**: Plotted with `PC1` and `PC2`.

### 4. **Model Comparison**
   - A composite plot was created to contrast:
     - The Elbow Curves for both the original and PCA-transformed data.
     - The clustering results for the original scaled data and the PCA data.

---

## Results

### Elbow Curve Analysis
- The Elbow Method identified the optimal value for `k` as **4** for both the original scaled data and the PCA-transformed data.

### Clustering Results
#### Original Scaled Data:
- Cryptocurrencies were clustered using the features:
  - `price_change_percentage_24h` (x-axis).
  - `price_change_percentage_7d` (y-axis).

#### PCA-Transformed Data:
- Cryptocurrencies were clustered using the first two principal components:
  - `PC1` (x-axis).
  - `PC2` (y-axis).

### Comparison of Results:
- The clustering results from both the original data and PCA-transformed data were visually similar.
- The PCA-based clustering simplified the data while maintaining the overall structure and separability of clusters.

---

## Summary

Using fewer features (via PCA) to cluster the data with K-Means had the following impacts:
- **Simplified the Data**: PCA reduced the dimensions from multiple features to three principal components, making the data easier to interpret.
- **Preserved Data Structure**: Despite using fewer features, the clusters formed using PCA were similar to those generated using the original scaled data.
- **Clearer Visualization**: The PCA scatter plot (PC1 vs. PC2) showed well-separated clusters, enhancing interpretability.

In conclusion, dimensionality reduction with PCA successfully simplified the data while retaining its essential information, resulting in effective clustering with K-Means.
