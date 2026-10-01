# E-Commerce Customer Segmentation Using K-Means Clustering and PCA

## Project Overview

This project applies unsupervised machine learning techniques to analyze customer behavior on an e-commerce platform. The main goal is to identify meaningful customer segments based on browsing, engagement, and purchasing behavior.

The analysis uses a publicly available e-commerce behavior dataset and focuses on a random sample of 50,000 unique customers.

## Business Objective

The main objective is to segment customers into meaningful behavioral groups that can support:

- Targeted marketing campaigns
- Personalized product recommendations
- Customer retention strategies
- Conversion improvement
- Loyalty programs

## Dataset

The project uses the **Multi-Category Store E-Commerce Behavior Dataset** available on Kaggle.

The original dataset contains user activity events such as:

- Product views
- Cart activity
- Purchases
- Product categories
- Brands
- Prices
- User sessions
- Event timestamps

A random sample of **50,000 unique users** was selected from the October 2019 dataset while retaining all activity records associated with those customers.

## Data Preparation

The main preprocessing steps included:

- Removing duplicate records
- Handling missing category and brand information
- Checking zero and negative prices
- Converting timestamps to datetime format
- Aggregating event-level data into customer-level features
- Examining feature correlations
- Identifying outliers using the IQR method
- Applying log transformation to reduce skewness
- Standardizing numerical variables using `StandardScaler`

## Customer Features

The final clustering model used the following customer-level features:

- Unique sessions
- Unique products viewed
- Unique categories viewed
- Active days
- Total cart events
- Total purchases
- Total views
- Total spending
- Average purchase value
- Events per session

## Exploratory Data Analysis

Exploratory analysis showed that customer behavior was strongly right-skewed. Most customers had relatively low activity, while a smaller group demonstrated substantially higher engagement and purchasing behavior.

Because extreme customer behavior could represent genuine high-value customers, outliers were retained rather than automatically removed.

## Clustering

The **K-Means clustering algorithm** was used to segment customers.

Several values of `k` from 2 to 8 were evaluated using:

- Elbow Method
- Silhouette Score
- Davies-Bouldin Index

The final model used three clusters.

Three clusters were selected because they provided a useful balance between cluster separation, compactness, and business interpretability.

## Model Evaluation

For the three-cluster solution:

- **Silhouette Score:** 0.474
- **Davies-Bouldin Index:** 0.992

These results indicate useful customer separation while allowing some overlap between behavioral groups.

## Customer Segments

### Cluster 0 - Engaged Browsers

Customers in this group browse frequently and explore multiple products but rarely complete purchases.

**Suggested strategy:**

- Personalized recommendations
- Conversion-focused promotions
- Browsing reminders
- Limited-time offers

### Cluster 1 - Low-Engagement Visitors

This is the largest customer group. These users have low session frequency, browsing activity, cart activity, and purchasing behavior.

**Suggested strategy:**

- Re-engagement campaigns
- Welcome promotions
- First-purchase discounts
- Personalized homepage content

### Cluster 2 - High-Value Customers

These customers demonstrate the highest purchasing activity, spending, and overall engagement.

**Suggested strategy:**

- Loyalty rewards
- VIP programs
- Personalized recommendations
- Exclusive promotions
- Customer retention campaigns

## Cluster Distribution

| Cluster | Customers | Percentage |
|---|---:|---:|
| Engaged Browsers | 13,403 | 26.81% |
| Low-Engagement Visitors | 31,145 | 62.29% |
| High-Value Customers | 5,452 | 10.90% |

## PCA Visualization

Principal Component Analysis (PCA) was used to reduce the customer features to two dimensions for visualization.

- PC1 explained approximately **55.24%** of the variance.
- PC2 explained approximately **24.25%** of the variance.
- Together, the first two components explained approximately **79.49%** of the total variance.

The PCA visualization showed clear behavioral differences among the three customer segments.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Machine Learning Techniques

- Exploratory Data Analysis
- Feature Engineering
- Log Transformation
- Feature Standardization
- K-Means Clustering
- Elbow Method
- Silhouette Analysis
- Davies-Bouldin Index
- Principal Component Analysis (PCA)

## Project Structure

```text
ecommerce-customer-segmentation/
│
├── ecommerce_customer_segmentation.ipynb
├── README.md
├── requirements.txt
├── report/
│   └── customer_segmentation_report.pdf
└── images/
    ├── elbow_method.png
    ├── pca_clusters.png
    ├── cluster_profile.png
    └── cluster_sizes.png