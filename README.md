# 🛍️ Customer Segmentation Clustering

An unsupervised machine learning project that segments mall customers into distinct groups based on their annual income and spending behavior, using K-Means clustering. Built with scikit-learn in a Jupyter notebook.

---

## 📌 Overview

This project analyzes customer demographic and behavioral data to uncover natural groupings in spending patterns — without any predefined labels. Using the classic elbow method to determine the optimal number of clusters, a K-Means model segments customers into 5 distinct groups based on their annual income and spending score, revealing actionable customer personas like high-income/high-spending and low-income/low-spending segments.

## ✨ Highlights

- 📊 Unsupervised segmentation using **K-Means clustering**
- 📈 Optimal cluster count (**k = 5**) determined via the **elbow method** (WCSS)
- 🎯 Clear visual separation of 5 customer segments by income and spending behavior
- 🖼️ Scatter plot visualization with labeled clusters and centroids

## 🖼️ Results

Cluster visualizations and output plots are available in the [`Results`](./Results) folder.

## 🧠 How It Works

### 1. Dataset

The project uses **`Mall_Customers.csv`** (in the [`dataset`](./dataset) folder) — a collection of **200 mall customer records**, containing:

| Column | Description |
|---|---|
| `CustomerID` | Unique identifier assigned to each customer |
| `Gender` | The gender of the customer |
| `Age` | The age of the customer in years |
| `Annual Income (k$)` | The customer's annual income, in thousands of dollars |
| `Spending Score (1-100)` | A score assigned by the mall based on customer behavior and spending patterns |

The dataset was confirmed complete — no missing values across any of the 200 records.

### 2. Feature Selection

Only two features were used for clustering: **`Annual Income (k$)`** and **`Spending Score (1-100)`**. This keeps the segmentation two-dimensional, which both simplifies the clustering task and makes the resulting customer segments easy to visualize and interpret on a single scatter plot.

### 3. Finding the Optimal Number of Clusters

K-Means requires the number of clusters (`k`) to be specified in advance, so the **elbow method** was used to find the best value:

- The **Within-Cluster Sum of Squares (WCSS)** — a measure of how tightly grouped the points are within each cluster — was calculated for `k = 1` through `k = 10`
- WCSS was plotted against `k`, producing an "elbow" graph where the rate of improvement sharply levels off
- The elbow point occurred at **k = 5**, indicating that 5 clusters best balance model simplicity against within-cluster tightness

### 4. Model Training

- **Algorithm:** K-Means (`init='k-means++'` for smarter centroid initialization, `random_state=42` for reproducibility)
- The model was fit directly on the 2D feature array (`Annual Income`, `Spending Score`) and assigned each of the 200 customers a cluster label (0–4) via `fit_predict`

### 5. Visualizing the Segments

The final scatter plot color-codes each customer by their assigned cluster and marks each cluster's centroid, revealing 5 clearly separated customer segments, including standout groups like:

- **High income, high spending** — top-tier, high-value customers
- **Low income, low spending** — budget-conscious customers
- **Moderate income, moderate spending** — the "average" customer segment
- Plus two additional segments capturing income/spending mismatches (e.g. high income but low spending, and vice versa) — often the most interesting groups for targeted marketing, since they represent untapped spending potential or price-sensitive high earners

## 🛠️ Tech Stack

- **Python**
- **pandas / numpy** — data processing
- **scikit-learn** — `KMeans`
- **matplotlib / seaborn** — elbow-method and cluster visualization
- **Jupyter Notebook**

## 📁 Project Structure

```
customer-segmentation-clustering/
├── customer_segmentation_clustering.ipynb   # Full preprocessing, clustering & visualization notebook
├── dataset/                                 # Raw dataset (Mall_Customers.csv)
├── Results/                                 # Screenshots/plots of clustering results
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Donna152/customer-segmentation-clustering.git
   cd customer-segmentation-clustering
   ```

2. Install the dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```

3. Launch the notebook:
   ```bash
   jupyter notebook customer_segmentation_clustering.ipynb
   ```

4. Run all cells to reproduce the elbow-method analysis, clustering, and visualization.

## 📓 Notebook

`customer_segmentation_clustering.ipynb` contains the full, step-by-step pipeline:
- Dataset loading and completeness check
- Feature selection (`Annual Income`, `Spending Score`)
- WCSS calculation and elbow-method visualization to determine the optimal cluster count
- K-Means model training and cluster label assignment
- Scatter plot visualization of the resulting customer segments with centroids

## 🔮 Possible Improvements

- Incorporate additional features (`Age`, `Gender`) into the clustering, using dimensionality reduction (e.g. PCA) to visualize higher-dimensional segments
- Validate the chosen `k` with additional metrics like the **silhouette score**, alongside the elbow method
- Profile each cluster with summary statistics (average age, gender split, income/spending ranges) to build actionable customer personas
- Compare K-Means against other clustering algorithms (e.g. DBSCAN, Hierarchical Clustering) to see if a different approach yields more meaningful segments
- Package the trained model to score new customers into existing segments in real time (e.g. via a simple Streamlit app)

## 📄 License

This project is intended for educational and portfolio purposes. The dataset used is the [Mall Customer Segmentation Data](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python), publicly available on Kaggle.
