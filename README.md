# R-La-Liga-2020-2021-MVP-Analysis
La Liga 2020-2021 MVP Analysis: Statistical Modeling of Top Performers

Project Title: Identifying the Most Valuable Player in La Liga's Top 4 Teams

Course: STAT 4194 - Advanced Data Analysis

Author: Chenchenyi Zhu

Date: April 2025

# ⚽ Overview
This project analyzes player performance from La Liga's top 4 teams (Atlético Madrid, Barcelona, Real Madrid, Sevilla) during the 2020-2021 season. Using unsupervised clustering and supervised learning, we identify Lionel Messi as the clear MVP while uncovering key performance drivers like expected goals (xG) and progressive passes.

🔗 Data Sources:

FBref Team Stats

Processed datasets for Atlético, Barcelona, Real Madrid, Sevilla

# 🔍 Key Findings
## 🏆 MVP Selection
Lionel Messi (Barcelona) dominated with:

30 goals (7 more than 2nd-place Karim Benzema)

0.94 correlation between actual and expected goals (xG)

Top-tier efficiency in goals/90min (0.87)

## 📊 Performance Drivers
| Metric               | Impact (Correlation) | Top Performer          |
|----------------------|----------------------|------------------------|
| Expected Goals (xG)  | 0.94                 | Messi (Barcelona)      |
| Progressive Passes   | 0.85                 | Manu Sánchez (Atlético)|
| Goals+Assists/90min  | 0.91                 | Luis Suárez (Atlético) |

## 📈 Model Insights
| Model               | RMSE  | Key Predictors                     |
|---------------------|-------|------------------------------------|
| Linear Regression   | 0.43  | xG, Progressive Passes             |
| XGBoost             | 5.90  | Progressive Passes, Minutes Played |
| K-means (k=4)       | -     | Cluster 4: Elite Scorers           |

# 🛠️ Methodology
## 1. Data Preprocessing
Combined stats from 4 teams (106 players)

Cleaned:

```r
liga$Min <- as.numeric(gsub(",", "", liga$Min))  
liga <- liga[complete.cases(liga), ]
```

## 2. Unsupervised Learning
K-means Clustering (k=4) revealed:

Cluster 4: Elite scorers (Messi, Benzema, Suárez)

Cluster 3: Low-efficiency players needing training

## 3. Supervised Learning
Linear Regression: xG was the strongest predictor (p < 2.2e-16)

XGBoost: Highlighted progressive passes' importance

# 🎯 Actionable Insights
For Coaches:

Build strategies around high-xG players

Develop progressive passing skills for midfielders

For Scouts:

Target players with xG > 10 and assists/90min > 0.3

Player Development:

Specialize Cluster 3 players in defensive/assist roles

# 🔧 Tools Used
R Libraries: ggplot2, caret, xgboost, factoextra

Clustering: K-means (Elbow Method)

Modeling: Linear Regression, XGBoost

Tags: #SportsAnalytics #LaLiga #MVP #ExpectedGoals #Clustering

Data sourced from FBref with custom feature engineering
