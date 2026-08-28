# Delivery ETA Prediction using Graph Analytics and Machine Learning

## Overview

This project develops a graph-enhanced ETA prediction system for logistics operations. Traditional ETA models rely primarily on routing and distance-based features, often ignoring the underlying transportation network structure. This project integrates graph analytics with machine learning to identify bottlenecks, analyze corridor risks, and improve ETA prediction accuracy.

---

## Problem Statement

Accurate ETA prediction is critical for logistics companies to:

- Improve customer satisfaction
- Reduce SLA breaches
- Optimize route planning
- Identify network bottlenecks
- Improve operational efficiency

The objective is to model delivery delays using route characteristics and graph-derived network intelligence.

---

## Dataset

The dataset contains logistics trip records with:

- 144,867 raw shipment records
- 14,817 unique trips
- 1,508 source hubs
- 1,481 destination hubs

Key attributes include:

- Actual delivery time
- OSRM estimated travel time
- Distance metrics
- Route type
- Source and destination hubs
- Timestamp information

---

## Methodology

### 1. Data Processing

- Data audit and quality assessment
- Missing value analysis
- OD leg aggregation
- Trip-level consolidation

### 2. Network Construction

A directed logistics graph was created where:

- Nodes represent logistics hubs
- Edges represent shipment corridors

Network Statistics:

- Nodes: 1,590
- Edges: 2,508

### 3. Bottleneck Detection

NetworkX was used to compute:

- Degree Centrality
- Betweenness Centrality
- In-Degree
- Out-Degree

Critical bottleneck hubs were identified based on centrality measures and SLA breach contribution.

### 4. Feature Engineering

Graph-derived features:

- Source hub centrality
- Destination hub centrality
- Corridor delay ratio
- Corridor traffic volume
- Network risk score

Temporal features:

- Hour of day
- Day of week
- Month

Operational features:

- OSRM time
- OSRM distance
- Actual distance to destination
- Route type

### 5. Machine Learning

Model:

- XGBoost Regressor

Two approaches were evaluated:

#### Baseline Model

Features:

- OSRM time
- OSRM distance
- Distance to destination
- Route type

#### Graph-Enhanced Model

Features:

- Baseline features
- Graph centrality metrics
- Corridor risk indicators
- Network bottleneck information

---

## Results

### Baseline Model

| Metric | Value  |
| ------ | ------ |
| MAE    | 47.12  |
| RMSE   | 108.40 |
| R²     | 0.9297 |

### Graph-Enhanced Model

| Metric        | Value  |
| ------------- | ------ |
| MAE           | 31.49  |
| RMSE          | 90.92  |
| R²            | 0.9506 |
| Accuracy @15% | 54.46% |

### Improvement

- MAE reduced by 33.17%
- RMSE reduced by 16.13%
- R² improved from 0.9297 to 0.9506

---

## Key Insights

1. Corridor delay ratio emerged as one of the most important predictive features.
2. Graph-based bottleneck indicators improved ETA prediction significantly.
3. High-centrality hubs contribute disproportionately to network-wide delays.
4. Integrating graph analytics with machine learning produces more accurate ETA estimates.

---

## Dashboard

The project includes an interactive Streamlit dashboard featuring:

- Model performance metrics
- Bottleneck hub analysis
- High-risk corridor analysis
- Feature importance visualization
- Comparative model evaluation

---

## Technologies Used

- Python
- Pandas
- NumPy
- NetworkX
- XGBoost
- Scikit-Learn
- Plotly
- Streamlit

---

## Project Structure

```text
Delivery_ETA/

├── dashboard/
├── notebooks/
├── outputs/
├── reports/
├── src/
├── data/

Outputs:
- node_metrics.csv
- corridor_metrics.csv
- top_bottlenecks.csv
- feature_importance.csv
- model_comparison.csv
- graph_model_results.csv
```

---

## Conclusion

A graph-enhanced ETA prediction framework was developed using logistics network analytics and machine learning. By incorporating corridor-level risk indicators and hub centrality measures, prediction accuracy improved substantially, achieving a 33.17% reduction in mean absolute error while maintaining strong generalization performance.
