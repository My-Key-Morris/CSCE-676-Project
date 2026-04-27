# Mining Frequent, Associative, and Sequential Patterns in MovieLens 25M

**CSCE 676 — Data Mining | Semester Project | Spring 2026**

This project investigates how analyst decisions — support thresholds, ranking metrics, and mining methods — shape the patterns extracted from MovieLens 25M (25 million movie ratings from 162,000 users). Three research questions test whether those choices produce meaningfully different results: they do, dramatically. Itemset counts span three orders of magnitude across a one-order threshold change, confidence and lift produce completely disjoint top-100 rule sets (Jaccard = 0), and sequential pattern mining adds no information beyond what unordered methods already capture.

**Start here:** [`main_notebook.ipynb`](main_notebook.ipynb)

**Project video:** (https://www.youtube.com/watch?v=2PY-TQO00dY)

---

## Research Questions

**RQ1 — Frequent Itemsets Under Varying Support.** What frequent itemsets emerge under different minimum support thresholds when user transactions are defined by positively rated movies (rating >= 4.0)?

**RQ2 — Confidence vs. Lift for Association Rules.** How do confidence and lift differ when evaluating association rules mined from positive user baskets?

**RQ3 — Sequential Patterns via PrefixSpan.** Do sequential patterns in user rating histories reveal structure that is missed by unordered frequent itemsets?

---

## Results Summary

**RQ1 (confirmed):** Itemset counts grow from 563 at support=0.10 to 410,690 at support=0.015. The content shifts systematically — blockbuster pairs at strict supports, niche cult-film triples at permissive supports. Support is a decision about what kind of content the model sees, not a tuning knob.

**RQ2 (confirmed, strongly):** Among 14,442 rules at support=0.05, the top-K-by-confidence and top-K-by-lift rankings share zero rules at K=10, 25, 50, and 100. Confidence-top rules all point at popular consequents (Godfather family, conf=0.966); lift-top rules are all franchise pairs (Harry Potter, lift=9.29). The two metrics are orthogonal.

**RQ3 (disconfirmed):** Across 4,412 sequential patterns at three PrefixSpan min_support levels, including all 383 of length >= 3, every pattern has a frequent unordered counterpart. Sequence ordering carries no non-redundant information on MovieLens rating timestamps.

---

## Dataset

**MovieLens 25M** — GroupLens Research, University of Minnesota
- 25,000,095 ratings from 162,541 users across 62,423 movies
- Download: https://grouplens.org/datasets/movielens/25m/
- Free for academic/non-commercial use under the GroupLens license

The dataset is too large to include in the repo. See [`data/README.md`](data/README.md) for download and setup instructions.

**Preprocessing:** Ratings >= 4.0 define "positive" baskets. The item vocabulary is pruned to the top 2,500 movies by distinct positive raters. 25,000 users are sampled for the basket matrix; 6,000 for the sequential analysis.

---

## How to Reproduce

This notebook was developed and executed locally on a Windows workstation (the earlier checkpoints ran on Google Colab, but the final analysis required more than Colab's 12 GB RAM cap).

1. Clone this repo
2. Download MovieLens 25M and place `ratings.csv` and `movies.csv` in `data/`
3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```
4. Update the `DATA_DIR` path in Section 4 of `main_notebook.ipynb` to point to your `data/` folder
5. Run the notebook top-to-bottom: **Kernel > Restart & Run All > Save**

Full runtime is approximately 25–30 minutes on a mid-range desktop; the RQ1 sweep at support=0.015 is the heaviest cell (~14 minutes).

---

## Key Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| Python | 3.10+ | Runtime |
| pandas | >= 2.0 | Data manipulation |
| numpy | >= 1.24 | Numerical computing |
| scipy | >= 1.10 | Sparse matrix construction |
| matplotlib | >= 3.7 | Visualization |
| mlxtend | >= 0.22 | Apriori, FP-Growth, association rules |
| prefixspan | >= 0.5.2 | Sequential pattern mining (PrefixSpan) |

Full dependency list: [`requirements.txt`](requirements.txt)

---

## Repository Structure

```
CSCE-676-Project/
├── main_notebook.ipynb          # Final deliverable — start here
├── requirements.txt             # Python dependencies
├── .gitignore
├── README.md                    # This file
├── checkpoints/
│   ├── checkpoint_1.ipynb       # Dataset selection & initial EDA
│   └── checkpoint_2.ipynb       # Research questions & preliminary analysis
└── data/
    ├── README.md                # Download instructions for MovieLens 25M
    ├── ratings.csv              # (not committed — download separately)
    └── movies.csv               # (not committed — download separately)
```

---

## References

- Han, J., Cheng, H., Xin, D., & Yan, X. (2007). Frequent pattern mining: current status and future directions.
- Pei, J. et al. (2001). PrefixSpan: Mining Sequential Patterns Efficiently by Prefix-Projected Pattern Growth. ICDE 2001.
- Raschka, S. mlxtend: https://rasbt.github.io/mlxtend/
- Gao, C. PrefixSpan-py: https://github.com/chuanconggao/PrefixSpan-py
- GroupLens. MovieLens 25M: https://grouplens.org/datasets/movielens/25m/
