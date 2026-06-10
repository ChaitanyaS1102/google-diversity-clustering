# Workforce Diversity Clustering Analysis

An unsupervised machine learning project exploring demographic patterns across U.S. industry sectors using K-Means clustering, PCA, and Shannon entropy — applied to gender and ethnicity workforce data.

---

## Project Overview

This project analyzes workforce diversity data to uncover structural demographic patterns across economic sectors. Using K-Means clustering and dimensionality reduction (PCA), the analysis addresses six core questions about how gender and ethnicity are distributed across industries, and which sectors cluster together based on their demographic compositions.

**Dataset:** `dataset-google.csv` — U.S. Bureau of Labor Statistics-style workforce data including gender percentages, ethnicity percentages, and total employment figures by sector and year.

---

## Research Questions

| # | Question |
|---|----------|
| Q1 | Which sectors have similar demographic structures across gender and ethnicity? |
| Q2 | Which three sectors are most gender-imbalanced, and how does that relate to total workforce size? |
| Q3 | How do gender balance and workforce size cluster together across sectors? |
| Q4 | Which sectors show the most extreme single-group ethnic dominance? |
| Q5 | Which sectors have the highest ethnic diversity, and how does this relate to sector size? |
| Q6 | Can we group industries based on similar ethnic compositions? |

---

## Methodology

### Features Used
- `percent_women`
- `percent_white`
- `percent_black_or_african_american`
- `percent_asian`
- `percent_hispanic_or_latino`
- `total_employed_in_thousands`

### Pipeline
1. **Data Cleaning** — Drop rows with missing demographic values
2. **Feature Engineering** — Log-transform employment size to reduce skew; normalize ethnicity percentages to 0–1 scale
3. **Scaling** — Z-score normalization via `StandardScaler` to equalize feature contributions
4. **Cluster Selection** — Elbow Method (SSE vs. k) to identify optimal k
5. **K-Means Clustering** — `n_clusters=4`, `random_state=42`, `n_init=10`
6. **Dimensionality Reduction** — PCA (2 components) for cluster visualization
7. **Diversity Scoring** — Shannon entropy across ethnic group proportions

---

## Key Findings

### Gender Clustering (Q2 & Q3)
- The Elbow Method indicated **k=4** as optimal for gender-based clustering
- **Cluster 1** captures large, predominantly male-dominated sectors (Manufacturing, Transportation)
- **Cluster 0** groups smaller sectors with moderate-to-high female representation
- The three most gender-imbalanced sectors (lowest `percent_women`) are concentrated in heavy industry

### Sector Distribution by Demographics (Q1)
- **Education and Health Services** clusters separately — consistent internal diversity structure
- **Manufacturing, Wholesale & Retail Trade** spread across multiple clusters
- **Niche sectors** (Mining, Construction, Agriculture) align into coherent but compact clusters

### Ethnicity-Based Clustering (Q6)
- **Cluster 1 (Construction)** emerges as a strong outlier — uniquely skewed ethnic composition (93.7% white)
- **Cluster 2** is the most diverse, capturing Leisure & Hospitality, Agriculture, and Public Administration
- **Cluster 0** includes moderate-diversity sectors: Manufacturing, Transportation, Public Administration
- PCA visualization confirms clear separation between Construction and the rest of the dataset

### Ethnic Diversity by Entropy (Q5)
- Construction, Other Services, and Professional & Business Services rank highest in ethnic diversity
- High-diversity sectors are not necessarily small — several large industries show strong demographic balance

---

## Visualizations

| Chart | Description |
|-------|-------------|
| `Elbow_Method_for_Optimal_k.png` | SSE curve used to select k=4 for gender clustering |
| `Gender_Balance_vs_Workforce_Size_Clustered.png` | Scatter plot of % women vs. total employed, colored by cluster |
| `Ethnicity-Based_Clustering_of_Industries_2023.png` | PCA scatter of ethnicity-based clusters (2023 data) |
| `Sector_Distribution.png` | Bar chart of sector counts per demographic cluster |

---

## Tech Stack

- **Python 3**
- **pandas** — data loading and manipulation
- **scikit-learn** — `KMeans`, `StandardScaler`, `PCA`
- **NumPy** — log transforms, entropy calculation
- **matplotlib / seaborn** — visualization
- **Jupyter Notebook** — interactive analysis

---

## Project Structure

```
├── diversity_clustering.ipynb     # Main analysis notebook
├── dataset-google.csv             # Source dataset
├── README.md
└── figures/
    ├── Elbow_Method_for_Optimal_k.png
    ├── Gender_Balance_vs_Workforce_Size_Clustered.png
    ├── Ethnicity-Based_Clustering_of_Industries_2023.png
    └── Sector_Distribution.png
```

---

## Limitations & Notes

- **Q4 normalization artifact:** After scaling ethnicity columns, some dominance share values fell below 1%, likely due to applying `idxmax`/`max` logic on already-scaled (non-interpretable) values. Dominance analysis should use raw percentages before normalization.
- Clustering is applied independently per question; cluster labels (0–3) are not consistent across questions.
- Data filtered to 2023 for ethnicity-based analysis (Q5, Q6) for consistency.

---

## Author

Fariha | MS Data Science, Seattle University  
[LinkedIn](#) · [GitHub](#)
