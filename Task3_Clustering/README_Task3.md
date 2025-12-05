📄 1. Project Overview

This project implements a complete end-to-end machine learning pipeline for customer clustering using unsupervised learning techniques.
The goal is to group credit card customers based on their spending behavior, payment patterns, and cash advance activity.

The dataset used contains features related to customer balance, purchase patterns, credit limits, payment behavior, and tenure.

This project was created as part of a Midterm Assignment – Machine Learning / Deep Learning.

🎯 2. Objectives
Main Objective

To design and implement a comprehensive clustering pipeline capable of segmenting customers into meaningful groups for business insight and decision-making.

Task Goals

Perform data cleaning & preprocessing

Handle missing values and outliers

Scale features properly

Apply unsupervised learning algorithms

Determine optimal number of clusters

Evaluate clusters (Silhouette Score, visual analysis)

Interpret and explain each customer segment

📂 3. Dataset Description

File: clusteringmidterm.csv

The dataset includes the following key features:

BALANCE — Outstanding balance

PURCHASES — Total purchase amount

ONEOFF_PURCHASES — Large one-time purchases

INSTALLMENTS_PURCHASES — Purchases using installment

CASH_ADVANCE — Total cash advance amount

PURCHASES_FREQUENCY, CASH_ADVANCE_FREQUENCY — Behavioral frequencies

CREDIT_LIMIT — Maximum credit

PAYMENTS & MINIMUM_PAYMENTS — Payment behavior

PRC_FULL_PAYMENT — Full payment ratio

TENURE — Customer duration (months)

🛠️ 4. Workflow
1. Load & Inspect Data

Checked missing values

Explored statistical distribution

Identified features requiring normalization

2. Preprocessing

Removed CUST_ID (non-feature)

Imputed missing values using Median Imputer

Standardized all numeric features using StandardScaler

Visualized outliers using boxplots

3. Optional Step: PCA

Performed PCA for 2D visualization

Helped understand cluster separations

4. Determine Optimal k

Used two methods:

✔ Elbow Method

Showed diminishing returns after k = 3–4.

✔ Silhouette Score

Peak score at k = 3 → best-defined clusters.

5. Clustering Model

Final model: K-Means with k = 3

Evaluation:

Silhouette Score indicates good separation

PCA visualization shows distinct cluster patterns

6. Cluster Interpretation

Created cluster profiles using normalized mean values per cluster and a heatmap.

🔍 5. Cluster Interpretation Summary
🔵 Cluster 0 — Active High Spenders

High purchases (one-off & installment)

High credit limit

Low cash advance usage

Good payment behavior

Long tenure

→ Premium, high-value customers with healthy financial behavior

🟣 Cluster 1 — Low Usage / Low Risk

Very low balance

Very low purchases & zero cash advance

Frequently pays full

Short tenure

→ Safe, low-risk customers with minimal card utilization

🟡 Cluster 2 — High Balance & High Cash Advance

Highest balance

High cash advance amount & frequency

Rarely pays in full

High credit limit utilization

Short tenure

→ Risky users; require monitoring due to heavy reliance on cash advance

📊 6. Visualizations

The notebook includes:

Missing value heatmap

Boxplots for outlier inspection

PCA scatter plots

Elbow & Silhouette evaluation plots

Cluster heatmap (feature normalization)

🧪 7. Technologies Used

Python

Pandas

NumPy

Scikit-Learn

Matplotlib

Seaborn

Google Colab
