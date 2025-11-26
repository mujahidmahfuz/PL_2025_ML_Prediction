# PL_2025_ML_Prediction
Here I used the Random Classifier to Predict the outcome of the 2025/26 Premier League season

# ⚽ Premier League 2025/26 Prediction using RandomForestClassifier

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow?logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML%20Model-orange?logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Visualization-Graphs-red?logo=matplotlib)
![Status](https://img.shields.io/badge/Project-Research%20Prototype-green)

---

## 📌 Project Overview

This project uses a **RandomForestClassifier** to predict the final **2025/26 Premier League standings** based on multiple historical Premier League seasons.

The model is trained using league summary statistics (points, wins, draws, losses, goals for/against, goal difference) from:


## The **2023/24 season** is used as the most recent feature set, and predictions are generated for all **20 clubs participating in 2025/26**, including the three promoted clubs:


Because these clubs did not play in 2023/24, their feature values are assigned as the **average of the bottom three clubs** from that season.

---

## 🧠 How the Model Works

### 1. Dataset Processing  
- Parses CSV match files such as:  
  `eng1_2018-19.csv, eng1_2019-20.csv, ..., eng1_2023-24.csv`  
- Each CSV contains **380 matches** (20 teams × 38 games)  
- Extracts:  
  - Goals and results from `FT` column  
  - Home & away points based on match outcomes  

### 2. Feature Engineering  
For each season, the script computes:  

| Feature         | Description                          |
|-----------------|--------------------------------------|
| points          | League points total                  |
| wins / draws / losses | Match outcomes               |
| goals_for / goals_against | Total goals scored/conceded |
| goal_diff       | Goals For − Goals Against            |
| position        | Final league ranking                 |

### 3. Machine Learning  

| Parameter     | Value                           |
|--------------|----------------------------------|
| Model         | RandomForestClassifier           |
| Trees         | 100                              |
| Max depth     | 8                                |
| Scaling       | StandardScaler                   |
| Class weight  | Balanced                         |
| Seed          | 42 (reproducible results)        |

Training predicts **season N+1 standings** using **season N features**.

---

## 📊 2025/26 Predictions (Expected Standings)

| Rank | Team             | Expected Position (mean) |
|------|------------------|--------------------------|
| 1    | Arsenal          | 1.43                     |
| 2    | Man City         | 2.23                     |
| 3    | Liverpool        | 4.59                     |
| 4    | Tottenham        | 6.15                     |
| 5    | Aston Villa      | 6.37                     |
| 6    | Chelsea          | 6.79                     |
| 7    | Newcastle        | 7.91                     |
| 8    | Man United       | 8.94                     |
| 9    | Everton          | 11.32                    |
| 10   | Brentford        | 12.05                    |
| 11   | Brighton         | 12.34                    |
| 12   | Crystal Palace   | 12.58                    |
| 13   | Wolves           | 12.69                    |
| 14   | Nott'm Forest    | 12.71                    |
| 15   | Bournemouth      | 12.92                    |
| 16   | Fulham           | 13.82                    |
| 17   | West Ham         | 14.83                    |
| 18   | Sheffield United | 15.19                    |
| 19   | Leeds United     | 15.96                    |
| 20   | Sunderland       | 15.96                    |

> ℹ️ *Lower “Expected Position (mean)” value → better predicted rank.*

---

## 📈 Visualization

The project generates a barplot showing expected positions (rank 1 = best):

```python
sns.barplot(x="expected_position", y="team", data=predictions)
plt.gca().invert_xaxis()
plt.savefig("results/predicted_league_table.png")




# PL_2025_ML_Prediction

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

**Predicting the 2025/26 Premier League season using a Random Classifier**

This repository contains a Jupyter notebook and season CSV datasets used to build a (baseline) random classifier that predicts match outcomes / season-related results for the 2025/26 Premier League season. The original repository files and notebook are hosted here. :contentReference[oaicite:0]{index=0}

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Files in this Repo](#files-in-this-repo)  
- [Quickstart — run the notebook](#quickstart---run-the-notebook)  
- [Dependencies](#dependencies)  
- [Data](#data)  
- [What the Notebook Does](#what-the-notebook-does)  
- [Results & Notes](#results--notes)  
- [Suggested Improvements](#suggested-improvements)  
- [Contributing](#contributing)  
- [License](#license)

---

## Project Overview

This project is a simple baseline ML exercise: using historic English Premier League season data (CSV files included) and a random classifier as a baseline to predict outcomes for the upcoming 2025/26 season. It demonstrates dataset loading, basic preprocessing, model training/evaluation (baseline), and a notebook-driven workflow. :contentReference[oaicite:1]{index=1}

---

## Files in this Repo

- `pl_2025_ml_prediction.ipynb` — Main Jupyter notebook (analysis, model, evaluation).  
- `eng1_2018-19.csv` — Historic season data (2018/19).  
- `eng1_2019-20.csv` — Historic season data (2019/20).  
- `eng1_2020-21.csv` — Historic season data (2020/21).  
- `eng1_2021-22.csv` — Historic season data (2021/22).  
- `eng1_2022-23.csv` — Historic season data (2022/23).  
- `eng1_2023-24.csv` — Historic season data (2023/24).  
- `LICENSE` — MIT License.

---

## Quickstart — run the notebook

1. **Clone the repo**
   ```bash
   git clone https://github.com/mujahidmahfuz/PL_2025_ML_Prediction.git
   cd PL_2025_ML_Prediction

