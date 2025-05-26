## 🎓 **Lecture 4: Introduction to Unsupervised Learning & Clustering**

**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. What is Unsupervised Learning?
2. What is Clustering?
3. Real-Life Applications of Clustering
4. K-Means Clustering Explained Simply
5. Python Implementation: Customer Grouping Example
6. Summary and Homework

---

### 1️⃣ **What is Unsupervised Learning?**

In **Unsupervised Learning**, the algorithm learns **patterns** from data **without labeled output**.

> 📌 The model **does not know the correct answers** — it only sees the input data and tries to find structure or similarity.

---

### 2️⃣ **What is Clustering?**

**Clustering** is the most common type of unsupervised learning.
It **groups similar data points together**.

> 🧠 Imagine you have 100 customers but don’t know anything about them. Clustering helps to group them into 2–3 types based on similar behavior (e.g., spending and income).

---

### 3️⃣ **Real-Life Examples of Clustering**

| Use Case                  | Description                                      |
| ------------------------- | ------------------------------------------------ |
| 🛍️ Customer Segmentation | Grouping customers based on buying habits        |
| 📚 Library Book Sorting   | Grouping books based on topics without labels    |
| 🧬 Biology                | Grouping genes with similar behavior             |
| 🗺️ Map Applications      | Grouping similar locations or points of interest |

---

### 4️⃣ **K-Means Clustering Explained**

**K-Means** is the most common clustering algorithm.

🧠 **How it works (simple steps):**

1. Choose how many clusters (e.g., K=2 or 3)
2. Randomly place “centers” (called centroids)
3. Assign each data point to the nearest center
4. Move the center to the average of points around it
5. Repeat steps 3–4 until the centers stop moving

---

### 5️⃣ **Python Example: Clustering Customers**

Let’s group customers by:

* **Income**
* **Spending Score** (how much they usually spend)

#### ✅ Step-by-Step Python Code

**Step 1: Import Libraries**

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
```

**Step 2: Create Example Data**

```python
data = {
    'Income': [15, 16, 17, 25, 30, 35, 85, 88, 90, 95],
    'Spending': [39, 40, 42, 50, 48, 55, 80, 83, 85, 90]
}
df = pd.DataFrame(data)
```

**Step 3: Apply K-Means Clustering**

```python
model = KMeans(n_clusters=2, random_state=0)
model.fit(df)
```

**Step 4: Add Cluster Labels to Data**

```python
df['Cluster'] = model.labels_
print(df)
```

**Step 5: Visualize Clusters**

```python
colors = ['red', 'blue']
for i in range(2):
    cluster = df[df['Cluster'] == i]
    plt.scatter(cluster['Income'], cluster['Spending'], color=colors[i], label=f'Cluster {i}')

plt.xlabel("Income (in thousands)")
plt.ylabel("Spending Score")
plt.title("Customer Clusters using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```

---

### 🔍 What the Output Shows

* **Cluster 0** → Low income, low spending
* **Cluster 1** → High income, high spending
* The model finds this pattern **without any labels**

---

### ✅ **Summary of Lecture 4**

* Unsupervised Learning learns patterns **without labels**
* Clustering groups similar data points automatically
* **K-Means** is an easy and effective clustering method
* You applied clustering to customer data and visualized it

---

### 🧠 Homework

1. Try changing the number of clusters to `3` or `4`
2. Use your own sample data (e.g., age and score of students)
3. Explore the `.cluster_centers_` attribute to see the cluster centers

```python
print(model.cluster_centers_)
```

4. Visualize using different colors or markers

