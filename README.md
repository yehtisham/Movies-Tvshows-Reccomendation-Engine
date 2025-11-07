# A Multi-Method Content-Based Recommendation System for Netflix

This project presents a **multi-signal, content-based recommendation engine** developed for Netflix data.  
It integrates multiple machine learning methods — **Cosine Similarity, k-Nearest Neighbors (kNN), Naïve Bayes, K-Means Clustering, and Apriori Association Rules** — to generate robust, personalized recommendations without relying on collaborative user-user data.

---

## Research Objective
To design and evaluate a **purely content-based** recommender system that:
- Incorporates **user likes/dislikes** and content metadata (genre, IMDb rating, release year).
- Leverages **multiple analytical methods** to overcome cold-start limitations.
- Produces **accurate, diverse, and explainable recommendations**.

---

## Methodology

### Data Source
Netflix dataset (~8,800 titles) collected from **Kaggle**, enriched with **IMDb ratings** fetched via the **OMDb API**.  
Key features:
- Title, Type (Movie/TV Show), Genre(s), Country, Director, Cast  
- IMDb Rating, Release Year, Duration, Description  

### Data Processing
- Cleaned missing values for director, cast, country, and ratings.  
- Parsed and one-hot encoded multiple genres using `MultiLabelBinarizer`.  
- Scaled numerical features (release year, IMDb ratings) with `MinMaxScaler`.  
- Created a **47-dimensional feature matrix** representing each title.

### Analytical Pipeline
| Step | Technique | Purpose |
|------|------------|----------|
| 1 | **Cosine Similarity** | Match user profile to content vectors |
| 2 | **k-Nearest Neighbors (kNN)** | Retrieve local neighborhood items |
| 3 | **Naïve Bayes** | Predict “like” probability (synthetic label) |
| 4 | **K-Means Clustering** | Identify preference clusters |
| 5 | **Apriori Association Rules** | Detect co-occurring genre patterns |
| 6 | **Ensemble Scoring** | Combine multiple signals into final rank |

---

## Ensemble Scoring Formula
\[
\text{Ensemble Score} =
w_{adj}(\text{Adjusted Similarity}) +
w_{nb}(\text{Naïve Bayes Score}) +
w_{cl}(\text{Cluster Score}) +
\text{Association Bonus}
\]

Typical weights: \( w_{adj}=0.4,\ w_{nb}=0.4,\ w_{cl}=0.2 \)

---

## Key Results

| Metric | Value |
|--------|-------|
| Naïve Bayes Accuracy | 0.84 |
| Precision / Recall / F1 | 0.54 / 0.59 / 0.57 |
| Optimal K (K-Means) | 4 |
| Silhouette Score | 0.659 |

- **Top Genres:** International Movies, Dramas, Comedies  
- **User Form Integration:** Google Forms + Sheets API to gather preferences  
- **Top Recommendations:** Balanced mix of high-rated, genre-aligned titles  

---

## Implementation Highlights
- Fully executed in **Python (Colab)** with **Pandas, Scikit-Learn, Seaborn, Matplotlib, MLxtend**.  
- Integrated with **Google Sheets API** for dynamic user input.  
- Ensemble logic allows smooth adaptation for **future hybrid systems**.

---

## Repository Structure
| Folder/File | Description |
|--------------|-------------|
| `Final.Research.Paper.pdf` | Complete academic report |
| `Netflix_MultiMethod_Recommendation.ipynb` | Implementation notebook |
| `Data/` | Cleaned and feature-engineered datasets |
| `Visuals/` | Genre and rating distribution plots |
| `README.md` | Project overview (this file) |

---

## 📚 References
- Goldberg et al., 1992 – Collaborative Filtering  
- Pazzani & Billsus, 2007 – Content-Based Recommendation Systems  
- Agrawal & Srikant, 1994 – Association Rule Mining  
- Gómez-Uribe & Hunt, 2015 – Netflix Recommender System  
- Kaggle Netflix Dataset (2020)  
- OMDb API (2020)

---

### 🏷️ Keywords
`Netflix` • `Content-Based Filtering` • `Recommender System` • `Machine Learning` • `kNN` • `Naïve Bayes` • `K-Means` • `Apriori` • `Python` • `Data Mining`
