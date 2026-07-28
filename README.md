# Assignment 7 — Customer Segmentation using K-Means Clustering and PCA

## Objective
To segment mall customers into distinct groups based on their annual income and spending behavior using **K-Means Clustering**, and to visualize these segments in two dimensions using **Principal Component Analysis (PCA)**. The resulting segments are intended to support targeted marketing strategies for the mall's management.

---

## Dataset

**Mall Customer Segmentation Dataset (Kaggle)**

Dataset Link: https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

The dataset contains 200 customer records with the following columns:

- `CustomerID` — unique customer identifier
- `Genre` — customer gender
- `Age` — customer age
- `Annual Income (k$)` — annual income in thousand dollars
- `Spending Score (1-100)` — score assigned based on spending behavior

> **Note:** The dataset file is not included in this repository. Download `Mall_Customers.csv` from the Kaggle link above and place it in the project root before running the program.

---

## Libraries Used

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

Modules from scikit-learn:

- `StandardScaler`
- `LabelEncoder`
- `KMeans`
- `PCA`

---

## Methodology

### 1. Data Understanding

- Loaded the dataset
- Displayed the first five records
- Identified numerical and categorical features
- Checked dataset information and descriptive statistics

### 2. Data Preprocessing

- Checked for missing values (none found)
- Dropped the `CustomerID` column
- Label-encoded the `Genre` column
- Standardized `Annual Income` and `Spending Score`

### 3. Model Development

- Applied the **Elbow Method** for K values from 1 to 10
- Selected the optimal number of clusters (**K = 5**)
- Trained the **K-Means** clustering model
- Assigned cluster labels to all customers
- Applied **PCA** to reduce features to two principal components

### 4. Visualization

Generated the following plots:

- Elbow curve
- Cluster scatter plot (Income vs Spending Score)
- PCA 2D visualization

### 5. Conclusion

Summarized customer segments, business applications, limitations of K-Means, and benefits of PCA.

---

## Results

- **Optimal clusters (K): 5**
- PCA reduced the standardized feature space to **2 dimensions** while preserving nearly all variance for visualization.

### Customer Segments

| Cluster | Avg. Income | Avg. Spending | Customer Profile |
|---------|--------------|----------------|------------------|
| 0 | Medium | Medium | Average customers |
| 1 | High | Low | Cautious high earners |
| 2 | Low | Low | Budget-conscious customers |
| 3 | High | High | Premium customers |
| 4 | Low | High | Value-seeking spenders |

*Cluster numbering may vary slightly between runs.*

---

## Output Files

- `elbow_curve.png`
- `cluster_scatter.png`
- `pca_visualization.png`

---

## Conclusion

K-Means clustering successfully identified five meaningful customer groups based on income and spending behavior. These segments can help mall management create targeted marketing campaigns, loyalty programs, and promotional strategies.

**Limitation of K-Means:** The number of clusters must be chosen in advance, and the algorithm assumes roughly spherical clusters.

**Advantage of PCA:** PCA reduces dimensionality while retaining most of the important information, making visualization and interpretation easier.

---

## How to Run

Install required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Run the Python script:

```bash
python Assignment-7.py
```

Or open the notebook:

```bash
jupyter notebook Assignment-7.ipynb
```

---

## Repository Structure

```text
Assignment_7/
│
├── Assignment-7.ipynb
├── README.md
├── elbow_curve.png
├── cluster_scatter.png
└── pca_visualization.png
```

---

