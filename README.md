# Taxi-Management-Clustering

![GitHub last commit](https://img.shields.io/github/last-commit/nhathpham/Taxi-Management-Clustering)
![contributors](https://img.shields.io/github/contributors/nhathpham/Taxi-Management-Clustering) 
![codesize](https://img.shields.io/github/languages/code-size/nhathpham/Taxi-Management-Clustering) 

For this mid-term project of class DS5230: Unsupervised Machine Learning, we formulated a problem statement and implemented various clustering methods on a selected dataset.

## Problem Statement

<img src="https://github.com/nhathpham/Scalable-Bird-Detection-Forecast/assets/87089936/a0cc4d69-a413-4f81-bf23-51cd6c03a762" width="300">

As head of a taxi company in Chicago, we want to optimize fleet distribution and taxi performance to boost efficiency and profitability.

**Challenge 1: Align fleet deployment with citywide demand**   
  ➡️ Cluster on spatial and temporal trip data to identify high-demand hotspots and patterns. Insights from this analysis will enable strategic fleet positioning, reduce response times, enhance customer satisfaction.

**Challenge 2:  Evaluate and improve efficiency of the fleet**   
  ➡️ Cluster taxis based on performance metrics to distinguish efficiency profiles. Insights from this analysis will enable interventions for low performers and adoption of best practices, enhance service quality and optimize costs.

## Dataset
- 1.7 million taxi trips in Chicago from September to November 2023. Each entry represents a trip and with 20+ attributes.
- Temporal features include start and end timestamps, rounded to the nearest 15 minutes. Spatial attributes include census tracts and community areas for pickup and dropoff locations with centroid coordinates. Spatial info is not available for locations outside Chicago.
- Additional attributes include taxi ID, trip duration, distance, fare, non-cash tips, tolls, extra charges, total cost, payment method, and associated taxi company.
- We queried this dataset from Google Big Query. The original dataset was provided by the City of Chicago.

## Code structure
```bash
├── Analysis 1
│   ├── trip_data_processing.ipynb
│   ├── trip_eda.ipynb
│   ├── trip_cluster_NP.ipynb
├── Analysis 2
│   ├── taxi_data_processing.ipynb
│   ├── taxi_eda.ipynb
│   ├── taxi_cluster.ipynb
├── Presentation
│   ├── Taxi_Management_Presentation.pdf
```

## Analysis 1: Trip Pattern Clustering


## Analysis 2: Taxi Performance Clustering
### 1. Data aggregation
- Aggregated trip data into profiles for 2,864 taxis
- Derived taxi attributes:
  - For clustering model: (median) Idle Time, Daily Use Rate, Trips per Day, Average Speed, Daily Revenue, Tips Proportion.
  - For later analysis: distribution of trips by pickup area, time of day, and payment type
    
### 2. Clustering 
- Implemented K-Means, GMM, Agglomerative Hierarchical, and HDBSCAN, with varying parameter and initialization tests.
- Baseline model:
  - RobustScaler() for feature scaling due to outliers; GMM with k=4 identifies the most distinct cluster.
  - Adjustment: removed outliers to address imbalanced clusters, and excluded Tips Proportion feature due to no variance.
- Final model:
  - StandardScaler() as features become more normal after adjustments
  - GMM with k=4 selected based on BIC, Silhouette scores, and testing different values of k

### 3. Results
We compared clusters against 5 performance metrics and analyzed additional features to derive the final conclusions for each cluster. For detailed results, please refer to the [Presentation](https://github.com/nhathpham/Taxi-Management-Clustering/blob/main/Taxi_Management_Presentation.pdf).

#### **Cluster 1: High Performers**
#### **Cluster 2: Urban Cabs**
#### **Cluster 3: Airport Cabs**
#### **Cluster 4: Low Performers**

