# Understanding AI — Virtual AI Learning Lab

An educational web application (Virtual AI Lab) that **visually teaches Machine Learning concepts** through interactive Streamlit apps. Deployed at [entendendo-ia.streamlit.app](https://entendendo-ia.streamlit.app).

## Apps

### Supervised Learning Lab (`app.py`)
6-step guided journey through supervised ML:
1. **Introduction** — what is supervised learning
2. **Data** — load CSV, explore columns
3. **Features** — select feature columns with checkboxes
4. **Train/Test Split** — adjustable split ratio slider
5. **Decision Tree** — train and visualize the tree (`plot_tree`)
6. **Inference** — predict on new data with interactive sliders

Includes accuracy evaluation and automatic column type detection (identification, features, label).

### Unsupervised Learning Lab (`app_clustering.py`)
Interactive K-Means clustering demonstration:
- Centroid animation during training
- Visual cluster assignments

### Datasets
| File | Description |
|------|-------------|
| `alunos.csv` | Student grade data |
| `usuarios_netflix.csv` | Netflix user behavior data |

CSV upload support for custom datasets.

## Tech Stack

Python, Streamlit, scikit-learn (DecisionTreeClassifier, KMeans), Pandas, Matplotlib, NumPy

## Architecture

Two independent Streamlit apps:
- `app.py` — Supervised learning (decision tree)
- `app_clustering.py` — Unsupervised learning (K-Means)

Each follows a step-based educational flow with a progress bar. Styled with custom CSS for educational feel (cards, chips, explanations).

## Setup

```bash
pip install streamlit pandas scikit-learn matplotlib numpy
streamlit run app.py     # Supervised Learning Lab
streamlit run app_clustering.py  # Clustering Lab
```

## Deployment

Auto-deployed on [Streamlit Cloud](https://streamlit.io/cloud).
