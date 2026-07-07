# Book Recommendation System: Collaborative Filtering & Cold-Start Strategy

## Objective
Design and evaluate a book recommendation engine for an online bookseller using collaborative filtering techniques, and translate model performance into actionable business strategy for personalization, marketing, and new-user onboarding.

## Business Problem
Recommendation quality directly drives conversion, retention, and revenue per user for any content or retail platform. This project evaluates multiple collaborative filtering approaches on a real user-book ratings dataset to identify which method delivers the most reliable recommendations, and designs a fallback strategy for new users with no rating history (the "cold-start" problem).

## Dataset
- 50 unique users, 20 unique books, ratings on a 1–5 scale
- User-item matrix sparsity: **20.70%** (relatively low), meaning enough overlapping interactions exist to support reliable neighborhood-based methods

## Methods Evaluated
| Method | Approach | RMSE |
|---|---|---|
| **User-Based CF (Cosine Similarity)** | Neighborhood-based, cosine distance | **1.2547 (best)** |
| User-Based CF (Pearson Correlation) | Neighborhood-based, linear correlation | Higher than Cosine |
| Matrix Factorization (SVD) | Latent factor model via Surprise library | ~0.93 (on Surprise's internal test split) |
| KNNWithMeans | Neighborhood-based with mean-centering | Highest RMSE among methods tested |

Additional components:
- **K-Means clustering** on the user-item matrix to segment users into behavioral groups (e.g., "High-Engagement Enthusiasts," "Consistent Readers") for targeted marketing
- **Cold-start handling** using popularity-based and highest-rated fallback recommendations for users with no rating history

## Key Business Insights & Recommendations

**1. Deploy User-Based CF with Cosine Similarity as the core recommendation engine**
It achieved the lowest RMSE (1.2547) among all methods tested, is more interpretable than SVD, and performs well given the dataset's low sparsity translating to more reliable recommendations and higher expected conversion from recommendation to purchase.

**2. Use K-Means clusters to power targeted marketing**
Distinct user segments emerged with different preference intensities (e.g., users who rate a narrow set of books very highly vs. users with broader, moderate preferences). This supports differentiated strategies: bundle deals and exclusive content for high-engagement segments, diversified recommendations and curated subscription boxes for broader-preference segments.

**3. Solve for cold-start with a popularity fallback**
New users with no rating history are shown top-rated, high-volume books first. This ensures a strong first impression and quickly collects the initial preference signal needed to transition them into personalized, model-based recommendations.

**Expected business impact:** higher conversion and revenue per user from more accurate recommendations, improved retention from a more personalized experience, and a smoother onboarding funnel for new users.

## Repository Structure
```
data/book_reviews.csv                     # user-book ratings dataset
notebooks/book_recommendation_CF.ipynb    # full analysis notebook
requirements.txt                          # Python dependencies
README.md
```

## Tools & Libraries
Python, pandas, NumPy, scikit-learn, Surprise (SVD, KNNWithMeans), seaborn, matplotlib

## Author
Raksha Chabhadia,
MBA Business Analytics
