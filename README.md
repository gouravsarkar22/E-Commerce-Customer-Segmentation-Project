# E-commerce-Customer-Segmentation-Project
Customer Segmentation on UK Online Retail Dataset 



# Project Overview

Customer segmentation is a crucial step for businesses to understand their customers better and design personalized marketing strategies or retentation campeigns. In this project, unsupervised machine learning techniques have been applied to segment customers from thr UK Online Reatail dataset based on their purchasing behavior. This project aggregates transaction 
data into RFM features and applies three clustering algorithms such as,

K-Means -> Partition-based clustering with elbow method for optimal k, good for spherical clusters.

Hierarchical (Agglomerative) Clustering -> Bottom-up approach with dendrogram visualization (hierarchical view) and cutting on the longest vertical line to find the optimal cluster value k, but slower.

DBSCAN -> Density-based clustering to handle noise and outliers. No k, but tunes eps/min_samples.


# Goal

The goal is to provide workflow that demonstrates best practices in unsupervised learning for e-commerce data. Obtain to group customers into meaningful clusters that can provide actionable business insights such as identifying high-value customers, loyal customers, and low-engagement customers. This project can be extended for production use, such as integrating
with marketing tools or deploying as a dashboard.


# Dataset

The dataset used is the Online Reatil UCI dataset from the UCI Machine Learning Repository. Transaction between 2010-2011 for a UK-based online retailer, including columns like InvoiceNO,
StockCode, Quantity, UnitPrice, CustomerID, and Country.

# Features Used 

*Recency* -> Days since last purchase. (Relative to a reference date)

*Frequency* -> Number of unique invoices.

*Monetary* -> Total spending per customer.


# Approach

1. *Data Cleaning & Preprocessing* : Removed cancelled transactions (negatives quantities) and duplicates. Focus on sales, not returns.
  
    Handled rows with missing CustomerID.
   
   Filtered columns with valid IDs.
   
   Focuses on positive sales and created RFM (Recency, Frequency, Monetary) features for the customers aggregation.
   
   Taking log transformed values for skewness for each of the features.
   
   Standardized the data for clustering

3. *Exploratory Data Analysis* : Comprehensive EDA to uncover distributions, outliers, and trends; such as

   -> Boxplots to find outliers and log-transformed distribution of Quantity, UnitPrice and TotalPrice.

   -> Categorical graph of top countries, i.e. geographical trend of sales.

   -> Popular products among the customers.

   -> Monthly, daily and hourly sales trends.

   ->Correlation heatmap among Quantity, UnitPrice and TotalPrice (To see how they are correlated to each other, positively/negatively).

   -> Unique customers distribution.


4. *Clustering Models Applied* :

   -> K-Means Clustering

   -> Hierarchical Clustering

   -> DBSCAN


5. *Model Evaluation* : Evaluated cluster quality using Silhouette Score, cluster summaries, and groupings of the customers.

   Adjusted optimal_k, n_clusters_hier, or eps on elbow/dendrogram/k-distance plots.

   Compared results across methods to identify the best-performing model among K-Means, Hierarchical (Ward Linkage), DBSCAN (eps tuning).
   

6. *Visualizations* :

   -> Elbow Curves for finding optimal k value for K-Means.

   -> Dendrograms for making cluster hierarchy.

   -> k-distance plot for DBSCAN eps tuning.

   -> PCA scatter plots.

   -> Pairwise RFM scatters with cluster centers.

7. **Descriptive Analysis** :

   -> Most of the purchases are from the United Kingdom.

   -> Most of the customers purchase in the afternoon time.

   -> Most of the customers have purchased items on Thursday, Wednesday, Tuesday.

   -> Most of the customers have purchased items in November, October, December, and the least number of purchases in April, January, February.


# Results & Conclusion 

-> K-Means (k=2) : Silhouette Score = 0.43 (Highest) 

-> Hierarchical (k=2) : Silhouette Score = 0.40 (Close tom K-Means)

-> DBSCAN (eps=0.5) : Silhouette Score = 0.29 (lower due to noise, but useful for anomaly detection)

 Since silhouette scores decreased when k>2, 2 clusters was chosen as optimal.


# Cluster Profiling

1. *Recency* :
   
   -> Cluster 1 (High-Value Customers) - Low (Purchased recently)

   -> Cluster 2 (Low-Value Customers) - High (Long time since last purchase)

3. *Frequency* :
   
   -> Cluster 1 (High-Value Customers) - High (Frequent buyers)

   -> Cluster 2 (Low-Value Customers) - Low (Occasional one-time buyers)

4. *Monetary* :
   
   -> Clister 1 (High-Value Customers) - High (Spend more per transaction)

   -> Clustomers 2 (Low-Value Customers) - Low (Spend less, irregular transactions)


# Key Insights

-> Cluster 1 : Loyal and profitable customers, contribute most of the revenue.

-> Cluster 2 : Less engaged or inactive customers with lower spending.

# Business Strategies

-> Retain Cluster 1 : Personalized offers, Sending cashbacks, Product updates, Premium benefits, Implement loyalty programs, Encourage and act on feedback.

-> Re-engage Cluster 2 : Off-season discounts, Targeted campaigns, Reactivation offers, Offer exceptional customer support, Use social media for engagement.


# Final Takeaway

This segmentation provides businesses with a clear understanding of customer groups and helping them to :

-> Focus resources on high-value customers.

-> Develop targeted strategies for low-value customers.

-> Improve overall customer retention and revenue growth.


# Tech Stack Used 

Python (Main Programming Language)

Pandas, NumPy (Data cleaning and feature engineering)

Matpkotkib, Seaborn (Visualizations)

Scikit-learn (Clustering algorithms & evaluation)




