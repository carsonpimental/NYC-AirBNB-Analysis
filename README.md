# NYC Airbnb Listing Performance Analysis

## Overview

This project analyzes New York City Airbnb listings to identify the key drivers of review quality, occupancy, and estimated revenue. Using clustering, statistical testing, and regression analysis, we segment listings into performance tiers and uncover which host, listing, and neighborhood characteristics are most strongly associated with high-performing listings.

The analysis is designed to support data-driven decision-making for hosts, platform operators, and consulting stakeholders by translating complex analytics into clear, actionable insights.

---

## Business Objective

Airbnb revenue growth is closely tied to booking demand, which is heavily influenced by review quality and guest experience. This project aims to answer:

* What differentiates high-rated listings from low-rated listings?
* Which factors drive higher occupancy and revenue?
* Should hosts focus on pricing strategies or quality improvements?

The ultimate goal is to provide evidence-based recommendations that improve listing performance and customer satisfaction.

---

## Data Source

| Item | Description |
|----|------------|
| Dataset | NYC Airbnb listings from Inside Airbnb |
| Update Frequency | Monthly |
| Snapshot Used | October 1, 2024 |
| Initial Size | 36,111 listings, 79 variables |
| Final Dataset | 53 variables after cleaning and transformation |

The dataset includes detailed information on host attributes, pricing, amenities, review scores, occupancy estimates, and neighborhood location.

---

## Data Preparation

### Cleaning and Filtering

* Dropped non-informative text and metadata fields
* Removed listings with missing review scores or revenue estimates
* Applied IQR-based outlier removal to estimated revenue
* Converted date, percentage, and currency fields into numeric formats

### Feature Engineering

* Created `host_years_active` from host join date
* Encoded categorical variables using dummy variables
* Converted ordered response-time categories into numeric scale
* Standardized review-related variables for clustering

---

## Analytical Approach

### Review-Based Clustering

To segment listings by performance quality, we clustered listings using review score dimensions:

* Accuracy
* Cleanliness
* Check-in
* Communication
* Location
* Value
* Overall rating

**Methods used:**
* StandardScaler for normalization
* K-Means clustering
* Elbow Method to select optimal k
* PCA for 2D visualization

### Review Clusters Identified

| Cluster | Description | Avg Rating |
|-------|------------|------------|
| Cluster 1 | Low Rating | ~2.47 |
| Cluster 2 | Mid Rating | ~4.37 |
| Cluster 3 | High Rating | ~4.85 |

---

## Statistical Testing and Modeling

### Techniques Used

* One-way ANOVA to test differences across clusters
* OLS regression to quantify relationships between review clusters, host experience, and performance
* PCA for dimensionality reduction and visualization

### Key Variables Tested

* Price
* Occupancy
* Number of reviews
* Host experience
* Neighborhood distribution

---

## Key Insights

### Insight 1: Review Quality Differences

* The largest performance gap between high- and low-rated listings is **perceived value**
* Accuracy, cleanliness, and communication also show meaningful separation
* Location differences exist but are less influential than service quality

### Insight 2: Leverage Hosting Experience

* Higher-rated listings have significantly more reviews (ANOVA p < 1e-50)
* Experienced hosts convert demand more effectively
* Review volume helps stabilize ratings and reduce the impact of outlier reviews

### Insight 3: Target Neighborhoods

* Manhattan has the highest proportion of low-rated listings and the lowest share of high-rated listings
* Staten Island shows the strongest concentration of high-rated listings
* Neighborhood composition plays a meaningful role in listing performance

### Insight 4: Demand Follows Quality, Not Price

| Metric | Result |
|------|--------|
| Price vs Review Cluster | Not statistically significant |
| Occupancy vs Review Cluster | Highly significant (p < 1e-60) |

Higher-performing listings do not charge more, but they are booked more frequently, leading to higher overall revenue.

---

## Recommendations

Based on the analysis:

* Focus on improving listing quality rather than adjusting price
* Invest in cleanliness, accuracy, and guest communication
* Encourage hosts to build long-term review volume
* Target underperforming neighborhoods with quality improvement initiatives
* Use review clusters as a framework for host education and platform optimization

---

## Tech Stack

| Category | Tools |
|--------|------|
| Language | Python |
| Data Analysis | pandas, NumPy |
| Visualization | matplotlib, seaborn |
| Clustering | scikit-learn (KMeans, PCA) |
| Statistics | scipy, statsmodels |
| Environment | Jupyter Notebook |

---

## Skills Demonstrated

* Data cleaning and feature engineering
* Unsupervised learning and clustering
* Statistical hypothesis testing (ANOVA)
* Regression analysis
* Translating analytics into consulting insights
* Communicating results to non-technical stakeholders

---

## Final Note

This project demonstrates how clustering and statistical analysis can be used to diagnose performance drivers in marketplace platforms. The framework is broadly applicable to other two-sided marketplaces where quality, reputation, and experience drive demand more strongly than price alone.
