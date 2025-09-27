

# Starbucks User Segmentation

## Project Overview

This project focuses on performing **unsupervised user segmentation** on Starbucks data to identify distinct user groups based on their demographic features, transaction behavior, and response to marketing offers. The goal is to provide actionable insights for optimizing future promotional strategies and personalize the customer experience.

The analysis follows a robust methodology, including extensive feature engineering, data transformation, and comparison of multiple clustering algorithms.

---

## Data Sources

The analysis begins with three initial raw datasets, typical of a customer segmentation problem:

1.  **`portfolio.json`**: Contains information about the 10 different offers (e.g., offer type, difficulty, reward, duration).
2.  **`profile.json`**: Contains demographic data for each customer (e.g., gender, age, income, membership start date).
3.  **`transcript.json`**: Contains all customer events (offers received, viewed, completed, and general transactions).

These three files were cleaned, merged, and transformed into a single feature matrix in the data processing phase.

---

## Project Structure

The repository is organized into two main Jupyter notebooks, detailing the complete data science pipeline:

1.  **`User_Segmentation_DataProcessing.ipynb`**
    * **Business and Data Understanding:** Initial exploration of the raw data (`portfolio`, `profile`, `transcript`).
    * **Data Preparation & Feature Engineering:** Cleaning, merging, and transforming the raw data into a consolidated **Customer-Offer-Engagement (COE)** matrix. This notebook concludes with a final dataset of **14,608 users** with **39 features**.
    * ***Output:*** `final_coe.csv` (ready for modeling).

2.  **`User_segmentation_Modelling&Evaluation.ipynb`**
    * **Preprocessing:** Applying **Power Transformation** to normalize data distributions and **Principal Component Analysis (PCA)** for dimensionality reduction.
    * **Modeling & Evaluation:** Application of clustering algorithms and determining the optimal number of clusters using the **Elbow Method** and **Silhouette Analysis**.
    * **Discussion & Conclusion:** Profiling the final customer segments and summarizing the findings.

---

## Methodology

### 1. Feature Engineering (Data Processing)
The primary notebook created a comprehensive feature set for each user, including:
* **Demographics:** Gender, age, income, and days since becoming a member (`days_member`).
* **Overall Transaction Metrics:** Total transactions (`txn_overall`) and total amount spent (`amt_overall`).
* **Offer Response Metrics:** Counts for offers received, viewed, and completed, broken down by offer type (BOGO, Discount, Informational).
* **Engagement Ratios:** Calculated fields like average spend per member day (`amt_per_member_day`) and RFM-style scores for promotional and non-promotional periods.

### 2. Modeling
The project explored two primary unsupervised learning techniques after transforming the data:
* **K-Means Clustering**
* **Gaussian Mixture Models (GMM)**

### 3. Key Findings
* The optimal number of clusters was determined to be **6 segments**, balancing statistical performance (Silhouette score) with practical business utility.
* The resulting segments are distinct and provide intuitive profiles for targeted marketing actions.

---

## Technologies and Dependencies

The project relies on a standard Python data science stack:

* **Python 3.x**
* **Core Libraries:** `pandas`, `numpy`, `json`
* **Machine Learning (Scikit-learn):** `KMeans`, `GaussianMixture`, `PCA`, `PowerTransformer`
* **Visualization:** `matplotlib.pyplot`, `seaborn`

---

## Files in this Repository

* `User_Segmentation_DataProcessing.ipynb`
* `User_segmentation_Modelling&Evaluation.ipynb`
* `final_coe.csv` (The aggregated dataset used for modeling)
* *Raw Data Files: `portfolio.json`, `profile.json`, `transcript.json` (Typically included or referenced externally)*
