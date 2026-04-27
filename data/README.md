# Data

This project uses the **MovieLens 25M** dataset from GroupLens (University of Minnesota).

The dataset is too large to include in the repository (~250 MB unzipped). To reproduce:

1. Download from: https://grouplens.org/datasets/movielens/25m/
2. Unzip so that `ratings.csv` and `movies.csv` are in this `data/` directory
3. Update the `DATA_DIR` path in `main_notebook.ipynb` (Section 4) to point here

The notebook expects two files:
- `ratings.csv` (25,000,095 rows: userId, movieId, rating, timestamp)
- `movies.csv` (62,423 rows: movieId, title, genres)
