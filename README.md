# Customer Segmentation & Marketing Strategy Analysis

## Project Overview:
- **Description:** This project performs an unsupervised learning analysis on a marketing campaign dataset to segment customers into distinct personas using PCA and Agglomerative Clustering. The goal is to derive actionable marketing strategies to improve campaign efficiency and revenue.
- **Outcome:** Four customer segments with recommended marketing strategies for each.

## Technologies & Libraries:
- **Language:** `Python 3.x`
- **Data Manipulation:** `pandas`, `numpy`, `datetime`
- **Visualization:** `matplotlib`, `seaborn`, `yellowbrick` (Elbow Method)
- **Machine Learning:** `scikit-learn`
	- **Preprocessing:** `LabelEncoder`, `StandardScaler`
	- **Decomposition:** `PCA`
	- **Clustering:** `KMeans` (for evaluation), `AgglomerativeClustering` (final model)

##  Dataset:
- **File:** `marketing_campaign.csv`
- **Format:** Tab-separated values (TSV) — use `sep="\t"` when loading.
- **Size:** 2,240 records, 29 features
- **Key Features:**
	- **Demographics:** `Year_Birth`, `Education`, `Marital_Status`, `Income`
	- **Household:** `Kidhome`, `Teenhome`
	- **Spending:** `MntWines`, `MntMeatProducts`, `MntGoldProds`, etc.
	- **Engagement:** `NumWebVisitsMonth`, `NumDealsPurchases`, `AcceptedCmp1-5`

## Methodology:
1. **Data Cleaning**
	 - **Null Handling:** Dropped rows with missing `Income` (24 rows removed).
	 - **Outlier Removal:** Removed unrealistic values (e.g., `Age > 90`, `Income > 600000`).
	 - **Date Parsing:** Converted `Dt_Customer` to `datetime` objects.

2. **Feature Engineering**
	 - **Age:** Derived from `Year_Birth`.
	 - **Spent:** Total sum across all product spending features.
	 - **Living_With:** Simplified `Marital_Status` into `Partner` or `Alone`.
	 - **Family_Size:** `Living_With` + children (`Kidhome + Teenhome`).
	 - **Is_Parent:** Binary flag (1 if children > 0).
	 - **Education:** Regrouped into `Undergraduate`, `Graduate`, `Postgraduate`.
	 - **Customer_For:** Number of days since the customer enrolled.

3. **Preprocessing & Dimensionality Reduction**
	 - **Encoding:** Label-encode categorical variables.
	 - **Scaling:** Normalize numerical features using `StandardScaler`.
	 - **PCA:** Reduce to 3 components to improve clustering performance and allow 3D visualization.

4. **Clustering Model**
	 - **Elbow Method:** Used (via `yellowbrick`) to evaluate cluster counts and determine optimal `k=4`.
	 - **Agglomerative Clustering:** Final model to segment customers into 4 clusters.

## Cluster Profiles & Strategic Insights
- **Cluster 0 — The Established Family** 
	- **Profile:** Older parents, typically with teenagers. Medium family size (2–4).
	- **Behavior:** Seek convenience and value.
	- **Strategy:** Value packs, multi-buy discounts, ready-made meal kits. Use a mix of traditional (flyers) and digital marketing.

- **Cluster 1 — The New Parents** 
	- **Profile:** Younger demographic, small families (usually one young child).
	- **Behavior:** Child-focused purchases.
	- **Strategy:** Promote fresh produce and organic baby products. Targeted social media and app-based personalized coupons.

- **Cluster 2 — The Elite Spenders** 
	- **Profile:** High income, no children (singles/couples).
	- **Behavior:** Highest spenders on wine and meat.
	- **Strategy:** Promote premium/gourmet items, emphasize exclusivity and quality, create curated "Gourmet Bundle" experiences.

- **Cluster 3 — The Budget Large Family** 
	- **Profile:** Older parents, large families (up to 5), lower income.
	- **Behavior:** Price-sensitive, deal seekers.
	- **Strategy:** Promote private-label and bulk packaging, push loyalty programs with immediate savings.

**Usage**
- **Install Dependencies:** Ensure required packages are installed.

```powershell
pip install pandas numpy matplotlib seaborn scikit-learn yellowbrick
```

- **Load Data:** Example to read the TSV dataset.

```python
import pandas as pd

df = pd.read_csv('marketing_campaign.csv', sep='\\t')
```

- **Run Analysis:** Execute your script (e.g., `analysis.py`) that performs cleaning, feature engineering, PCA, clustering, and visualization. Example:

```powershell
python analysis.py
```

**Visualizations Included**
- **3D Scatter Plot:** Visualizes 3 PCA components colored by cluster.
<img width="645" height="658" alt="The Plot of The Clusters" src="https://github.com/user-attachments/assets/29c6a05b-11e3-4504-9950-5825c8e4dbfa" />

- **Elbow Plot:** Shows explained variance / clustering inertia to validate cluster count.
<img width="789" height="516" alt="Elbow Method to Determine the Number of Clusters to be Formed" src="https://github.com/user-attachments/assets/71de50e8-e810-4342-8655-55e721c81449" />

- **Cluster Profiling:** Boxplots and swarmplots for `Income` vs. spending per cluster.
<img width="695" height="516" alt="Number of Deals Purchased" src="https://github.com/user-attachments/assets/6a3dd3ea-8c88-4a78-bc33-626ad535e707" />

- **Campaign Acceptance:** Countplots showing which clusters accept promotions (AcceptedCmp1–5).
<img width="704" height="516" alt="Count of Promotions Accepted" src="https://github.com/user-attachments/assets/2feab4e7-d2df-4c84-96a4-ce6a417fdb98" />


**Files & Scripts (suggested structure)**
- `marketing_campaign.csv` — dataset (TSV)
- `analysis.py` — main script to run preprocessing, PCA, clustering, and generate plots
- `utils.py` — (optional) helper functions for feature engineering and plotting
- `outputs/` — folder to save generated figures and cluster summary CSVs

**Next Steps / Suggestions**
- Add the `analysis.py` script to this repo if you want me to implement the full pipeline here.
- I can also generate sample code snippets for each step (cleaning, feature engineering, PCA, clustering, visualization) and commit them to the workspace.

---

**Contact**
- **Name:** Loay Ayman
- **🔗 LinkedIn:** linkedin.com/in/loayayman 







