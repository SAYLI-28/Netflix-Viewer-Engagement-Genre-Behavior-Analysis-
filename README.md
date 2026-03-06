🎬 Netflix Viewer Engagement & Genre Behaviour Analysis

> A **Python-based exploratory data analysis** project examining content patterns and viewing behaviour across Netflix titles — revealing genre distribution, content type split, duration outliers, and actionable insights for content strategy.

📌 **Built for:** Data Analyst Portfolio | Remote Jobs | Business Intelligence Roles  
🛠️ **Tools:** Python · pandas · NumPy · Matplotlib · seaborn  
📁 **Dataset:** Kaggle — Netflix Movies and TV Shows Dataset

---

## 🎯 Business Problem

Netflix's content and recommendation teams need to understand:
- **What is the content mix** — how many movies vs TV shows?
- **Which genres dominate** the Netflix catalogue?
- **Where are the duration outliers** — unusually long titles that skew averages?
- **What patterns** should inform content acquisition and recommendation strategy?

---

## 📊 Real Findings From This Analysis

| Finding | Value |
|---------|-------|
| 🎬 Movies vs TV Shows | **69.6% Movies** / 30.4% TV Shows |
| 🏆 Most Popular Genre | **International Movies** (~2,700 titles) |
| 🥈 Second Genre | **Dramas** (~2,400 titles) |
| 🥉 Third Genre | **Comedies** (~1,650 titles) |
| ⏱️ Longest Movie | **'Once Upon a Time in America' — 229 minutes** |
| 📦 Typical Movie Duration | **90–110 minutes** (IQR range) |
| ⚠️ Outliers Detected | Movies exceeding **150+ minutes** — flagged via IQR method |
| 📅 Most Recent Titles | 2021 releases — Ali & Ratu Ratu Queens, Sweet & Sour, Xtreme |

---

## 📈 Visualisations Built

### Chart 1 — Content Type Distribution (Pie Chart)
*Movies dominate at 69.6% vs TV Shows at 30.4%*

![Netflix Content Split](NETFLIX%20CONTENT%20PIE%20CHART%20.png)

---

### Chart 2 — Top 10 Netflix Genres (Bar Chart)
*International Movies leads, followed by Dramas, Comedies, and International TV Shows*

![Popular Netflix Genres](POPULAR%20NETFLIX%20GENRES.png)

---

### Chart 3 — Movie Duration Outlier Detection (Box Plot)
*IQR method identifies movies above 150 min as statistical outliers — 229 min being the most extreme*

![Outlier Detection](OUTLIERS%20PLOTS%20.png)

---

### Chart 4 — Final Conclusions & Insights
*Summary of all key findings from the analysis*

![Final Outcome](FINAL%20OUTCOME.png)

---

## 🧹 Data Cleaning & Outlier Detection

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('netflix_titles.csv')

# Basic inspection
print(df.shape)
print(df.isnull().sum())
print(df.dtypes)

# Fill or drop nulls
df.dropna(subset=['type', 'listed_in', 'duration'], inplace=True)

# Separate movies from TV shows
movies = df[df['type'] == 'Movie'].copy()
tv_shows = df[df['type'] == 'TV Show'].copy()

# Convert duration to numeric for movies
movies['duration_mins'] = movies['duration'].str.replace(' min','').astype(int)

# IQR-based outlier detection on movie duration
Q1 = movies['duration_mins'].quantile(0.25)
Q3 = movies['duration_mins'].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = movies[movies['duration_mins'] > upper_bound]
print(f"Outlier movies detected: {len(outliers)}")
print(f"Longest outlier: {movies['duration_mins'].max()} mins")
```

---

## 📋 Analysis Workflow

```
Raw Netflix Dataset (Kaggle)
        ↓
Data Loading & Inspection
(shape, dtypes, null counts, duplicates)
        ↓
Data Cleaning
(null handling, type conversion, duration parsing)
        ↓
Content Split Analysis
(Movie 69.6% vs TV Show 30.4%)
        ↓
Genre Distribution Analysis
(Top 10 genres by title count)
        ↓
Outlier Detection — IQR Method
(Flag unusually long movies above 150 mins)
        ↓
Recency Analysis
(Newest titles by release year)
        ↓
Final Conclusions & Business Recommendations
```

---

## 💡 Business Insights & Recommendations

1. **Movies dominate at 69.6%** — Netflix is movie-heavy; TV show content acquisition could be increased to balance the catalogue and improve series binge behaviour
2. **International Movies is the #1 genre** — global content strategy is working; this should be reflected in recommendation weighting for non-English speaking markets
3. **Dramas at #2 confirms long-form storytelling preference** — drama acquisitions and originals should remain a priority in content budget
4. **Outlier movies above 150 mins** need special treatment in recommendation engines — standard watch-time models should not penalise these unfairly
5. **Documentary and Action & Adventure in Top 5** suggest both educational and high-energy content have strong demand — a balanced recommendation mix across these should reduce churn

---

## 🛠️ Tech Stack

| Tool | Usage |
|------|-------|
| Python 3 | Core language |
| pandas | Data loading, cleaning, filtering, grouping |
| NumPy | IQR calculation, numerical operations |
| Matplotlib | Bar charts, pie charts, box plots |
| seaborn | Statistical visualisation styling |
| Jupyter Notebook | Development & presentation environment |

---

## 🚀 How to Run This Project

```bash
# 1. Clone the repo
git clone https://github.com/SAYLI-28/Netflix-Viewer-Engagement-Genre-Behavior-Analysis.git

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open notebook
jupyter notebook Netflix_Analysis.ipynb
```

---

## 📦 requirements.txt

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
jupyter>=1.0.0
```

---

## 📁 Files in This Repo

| File | Description |
|------|-------------|
| `Netflix_Analysis.ipynb` | Full Jupyter notebook with analysis |
| `requirements.txt` | Python dependencies |
| `NETFLIX%20CONTENT%20PIE%20CHART%20.png` | Movies vs TV Shows split |
| `POPULAR%20NETFLIX%20GENRES.png` | Top 10 genres bar chart |
| `OUTLIERS%20PLOTS%20.png` | Movie duration box plot |
| `FINAL%20OUTCOME.png` | Final conclusions output |
| `README.md` | This file |

---

## 👩‍💻 About

Built by **Sayli Markandey** — Junior Data Analyst  
📧 saylimarkandey@gmail.com  
🐙 [github.com/SAYLI-28](https://github.com/SAYLI-28)

*Open to remote Data Analyst opportunities globally.*

---

⭐ If this project was useful, consider starring the repo!
