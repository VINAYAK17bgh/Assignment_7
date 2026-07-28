# Assignment 7 — Customer Segmentation using K-Means Clustering and PCA

## Objective
To segment mall customers into distinct groups based on their annual income and
spending behavior using **K-Means Clustering**, and to visualize these segments
in two dimensions using **Principal Component Analysis (PCA)**. The resulting
segments are intended to support targeted marketing strategies for the mall's
management.

## Dataset
**Mall Customer Segmentation Dataset** (Kaggle)
🔗 https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

The dataset contains 200 records with the following columns:
- `CustomerID` — unique identifier
- `Genre` — customer gender
- `Age` — customer age
- `Annual Income (k$)` — annual income in thousands of dollars
- `Spending Score (1-100)` — score assigned based on spending behavior

> **Note:** The raw dataset is **not included** in this repository per the
> submission instructions. Please download `Mall_Customers.csv` from the
> Kaggle link above and place it in the project root before running the code.

## Libraries Used
- `pandas` — data loading and manipulation
- `numpy` — numerical operations
- `matplotlib` / `seaborn` — visualization
- `scikit-learn` — `StandardScaler`, `LabelEncoder`, `KMeans`, `PCA`

## Methodology
1. **Data Understanding** — Loaded the dataset, inspected the first five
   records, identified numerical (`Age`, `Annual Income`, `Spending Score`)
   and categorical (`Genre`) features, and reviewed dataset info/statistics.
2. **Data Preprocessing** — Checked for missing values (none found), dropped
   the `CustomerID` column, label-encoded `Genre`, and standardized the
   numerical features (`Annual Income`, `Spending Score`) using `StandardScaler`.
3. **Model Development**
   - Used the **Elbow Method** (K = 1 to 10) to identify the optimal number
     of clusters based on inertia.
   - Trained a final **K-Means** model with the selected K (K = 5) and
     assigned cluster labels to each customer.
   - Applied **PCA** to reduce the standardized features to 2 principal
     components for visualization.
4. **Visualization and Evaluation** — Plotted the elbow curve, a scatter plot
   of clusters on the original feature space (Income vs Spending Score), and
   a PCA-based 2D scatter plot colored by cluster label.
5. **Conclusion** — Summarized findings, business use cases, one limitation
   of K-Means, and one advantage of PCA.

## Results
- **Optimal number of clusters (K):** 5, determined via the elbow curve.
- **PCA:** The 2 principal components together explain effectively all of
  the variance in the (2-feature) standardized data used for clustering.
- **Identified segments:**

| Cluster | Avg. Income | Avg. Spending Score | Profile |
|---------|-------------|----------------------|---------|
| 0 | Mid | Mid | Average / typical customers |
| 1 | High | Low | Cautious high-earners (under-targeted) |
| 2 | Low | Low | Budget-conscious shoppers |
| 3 | High | High | Premium, most valuable customers |
| 4 | Low | High | Value-seeking spenders |

*(Exact cluster order/labels may vary slightly by run; see `customer_segments_output.csv` for the actual run's assignments.)*

Generated visualizations:
- `elbow_curve.png` — Elbow Method plot for choosing K
- `cluster_scatter.png` — Customer segments on Income vs Spending Score
- `pca_visualization.png` — Clusters projected onto 2 PCA components

## Conclusion
This project applied K-Means clustering to segment mall customers based on
their annual income and spending score, identifying five distinct groups
ranging from low-income budget shoppers to high-income premium spenders. The
Elbow Method confirmed five clusters as the optimal choice, and PCA was used
to project the data into two dimensions for clear visualization, showing
well-separated, meaningful segments. From a business perspective, these
segments enable the mall's management to design targeted marketing
campaigns — for example, loyalty rewards for high-income/high-spending
customers and promotional offers to convert high-income/low-spending
customers into active spenders. A key limitation of K-Means is that it
requires the number of clusters (K) to be specified in advance and assumes
spherical, similarly-sized clusters, which may not always reflect real
customer behavior. An advantage of PCA is that it reduces dimensionality
while retaining most of the data's variance, making complex, multi-feature
customer data easier to visualize and interpret without significant loss
of information.

## How to Run
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
python Assignment-7.py
# or open Assignment-7.ipynb in Jupyter and run all cells
```

## Repository Structure
```
├── Assignment-7.ipynb          # Main notebook (all 4 tasks)            
├── README.md                   # This file
├── elbow_curve.png             # Output plot
├── cluster_scatter.png         # Output plot
└── pca_visualization.png       # Output plot
```
