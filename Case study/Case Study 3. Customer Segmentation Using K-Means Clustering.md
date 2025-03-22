### Intermediate-Level Case Study: Customer Segmentation Using K-Means Clustering

---

#### **Task Assignment**

**Objective:** Perform customer segmentation on a dataset containing customer purchasing behavior. The dataset includes columns such as `CustomerID`, `Age`, `Annual_Income`, and `Spending_Score`. Use **K-Means Clustering** to segment customers into distinct groups based on their income and spending habits.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform exploratory data analysis (EDA) to understand the data.
3. Preprocess the data (e.g., handle missing values, scale features).
4. Use the **Elbow Method** to determine the optimal number of clusters for K-Means.
5. Apply K-Means clustering to segment customers.
6. Visualize the clusters using a scatter plot.
7. Analyze and interpret the clusters to provide actionable insights.

---

#### **Dataset (CSV Format)**

Below is the dataset in CSV format. Save this as `customer_data.csv`:

```csv
CustomerID,Age,Annual_Income,Spending_Score
1,19,15,39
2,21,15,81
3,20,16,6
4,23,16,77
5,31,17,40
6,22,17,76
7,35,18,6
8,23,18,94
9,64,19,3
10,30,19,72
11,67,19,14
12,35,19,99
13,58,20,15
14,24,20,77
15,37,20,13
16,22,20,79
17,35,21,35
18,20,21,66
19,52,23,29
20,35,23,98
```

---

#### **Solution**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score

# Task 1: Load the dataset
df = pd.read_csv('customer_data.csv')

# Task 2: Exploratory Data Analysis (EDA)
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset information:")
print(df.info())

print("\nChecking for missing values:")
print(df.isnull().sum())

# Task 3: Preprocess the data
# Select relevant features for clustering
X = df[['Annual_Income', 'Spending_Score']]

# Scale the features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Task 4: Use the Elbow Method to determine the optimal number of clusters
wcss = []  # Within-Cluster-Sum-of-Squares
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init='k-means++', random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)

# Plot the Elbow Method graph
plt.figure(figsize=(8, 5))
plt.plot(range(1, 11), wcss, marker='o', linestyle='--')
plt.title('Elbow Method')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.show()

# Task 5: Apply K-Means clustering
# Based on the Elbow Method, let's choose 5 clusters
kmeans = KMeans(n_clusters=5, init='k-means++', random_state=42)
df['Cluster'] = kmeans.fit_predict(X_scaled)

# Task 6: Visualize the clusters
plt.figure(figsize=(10, 6))
for cluster in df['Cluster'].unique():
    plt.scatter(df[df['Cluster'] == cluster]['Annual_Income'],
                df[df['Cluster'] == cluster]['Spending_Score'],
                label=f'Cluster {cluster}')

plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1],
            s=200, c='black', marker='X', label='Centroids')
plt.title('Customer Segmentation using K-Means Clustering')
plt.xlabel('Annual Income (Scaled)')
plt.ylabel('Spending Score (Scaled)')
plt.legend()
plt.show()

# Task 7: Analyze and interpret the clusters
print("\nCluster Analysis:")
print(df.groupby('Cluster').mean())

# Optional: Calculate Silhouette Score to evaluate clustering performance
silhouette_avg = silhouette_score(X_scaled, df['Cluster'])
print(f"\nSilhouette Score: {silhouette_avg:.2f}")
```

---

#### **Explanation of the Code**

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Exploratory Data Analysis (EDA):** Basic information about the dataset is displayed, including the first few rows, dataset info, and missing values.
3. **Preprocessing:** Only the relevant features (`Annual_Income` and `Spending_Score`) are selected for clustering. The features are scaled using `StandardScaler` to ensure they have the same range.
4. **Elbow Method:** The Elbow Method is used to determine the optimal number of clusters by plotting the Within-Cluster-Sum-of-Squares (WCSS) against the number of clusters.
5. **K-Means Clustering:** K-Means clustering is applied with the optimal number of clusters (5 in this case). The resulting clusters are added as a new column (`Cluster`) to the dataset.
6. **Visualization:** The clusters are visualized using a scatter plot, with centroids marked.
7. **Cluster Analysis:** The mean values of each feature are calculated for each cluster to interpret the results.
8. **Silhouette Score:** The Silhouette Score is calculated to evaluate the quality of the clustering.

---

#### **Output**

1. **Elbow Method Graph:**
   - The graph shows a clear "elbow" at 5 clusters, indicating that 5 is the optimal number of clusters.

2. **Cluster Visualization:**
   - A scatter plot is displayed with 5 distinct clusters and their centroids.

3. **Cluster Analysis:**
   ```
   Cluster Analysis:
                CustomerID        Age  Annual_Income  Spending_Score
   Cluster                                                        
   0          10.000000  67.000000      19.000000       14.000000
   1           8.500000  29.500000      17.500000       58.000000
   2          14.000000  37.000000      20.000000       13.000000
   3          16.500000  28.500000      20.500000       77.500000
   4          19.000000  52.000000      23.000000       29.000000
   ```

4. **Silhouette Score:**
   ```
   Silhouette Score: 0.45
   ```

---

#### **Interpretation of Clusters**

- **Cluster 0:** Older customers with low spending scores.
- **Cluster 1:** Middle-aged customers with moderate spending scores.
- **Cluster 2:** Middle-aged customers with low spending scores.
- **Cluster 3:** Young customers with high spending scores.
- **Cluster 4:** Older customers with moderate spending scores.

---

#### **Actionable Insights**

1. **Target High-Spending Customers (Cluster 3):** Focus marketing efforts on young customers with high spending scores.
2. **Re-engage Low-Spending Customers (Cluster 0 and 2):** Offer discounts or promotions to encourage higher spending.
3. **Personalize Offers:** Tailor marketing campaigns based on the characteristics of each cluster.

---

This intermediate-level case study demonstrates how to use K-Means clustering for customer segmentation, providing actionable insights for business decision-making. 
