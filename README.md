[README.md](https://github.com/user-attachments/files/32217907/README.md)
# X (Twitter) Data Analysis & Hypothesis Testing

## **Abstract**
This project investigates key drivers of engagement on X (formerly Twitter) using the X API v2. By analyzing real-world tweet datasets across high-profile accounts, we formulate and test three hypotheses concerning posting time, bookmark counts, and tweet character length. Non-parametric and parametric tests reveal that bookmark volume and tweet length significantly increase engagement, whereas time-of-day posting windows do not show a statistically significant effect.

---

## 📂 Repository Structure

| File / Folder | Description |
|---|---|
| **`X_API_Hypothesis_Research.pdf`** | Presentation slides summarizing data collection, preprocessing, hypothesis tests, and conclusions |
| **`Research_Question1_2.ipynb`** | Analysis and statistical testing for H1 (Posting Time vs. Engagement Rate) & H2 (Bookmarks vs. Likes) |
| **`Research_Question_3.ipynb`** | Analysis and statistical testing for H3 (Tweet Length vs. Likes) |
| **`Data/`** | Raw and merged tweet CSV datasets (`google_tweets.csv`, `tesla_tweets.csv`, etc.) |

---

## 📊 Dataset Description

- **Collection Tool:** X API v2 (`/2/users/{id}/tweets`)
- **Accounts Tracked:** High-profile brands and public figures (Google, Tesla, McDonald's, Wendy's, Starbucks, Fabrizio Romano, Donald Trump)
- **Sample Size:** 696 raw tweets merged across accounts

### Preprocessing Steps
- Removed unindexed tweets with **0 impressions** (`public_metrics.impression_count == 0`)
- Computed **Engagement Rate** = $(\text{replies} + \text{retweets} + \text{likes} + \text{quotes} + \text{bookmarks}) / \text{impressions}$
- Grouped posting hours into 4 windows: **Morning** (05:00–11:00), **Afternoon** (12:00–17:00), **Evening** (18:00–22:00), **Night** (23:00–04:00)
- Handled viral skewness with **IQR outlier filtering** ($1.5 \times \text{IQR}$) per time group
- Measured tweet length in characters (`len(text)`)

---

## 🧪 Hypotheses & Findings

| Hypothesis | Research Question | Statistical Test | p-value | Conclusion |
|---|---|---|---:|---|
| **H1** | How does posting time (hour of the day) affect tweet engagement rate? | Kruskal–Wallis | 0.1310 (>0.05) | **Fail to reject H₀** — No statistically significant difference in engagement rates across posting time groups |
| **H2** | Do tweets with higher bookmark counts receive more likes? | Mann–Whitney U | $4.28 \times 10^{-97}$ (<0.05) | **Reject H₀** — Tweets with higher bookmark counts receive significantly more likes |
| **H3** | Does tweet character length affect user engagement (likes)? | One-tailed Welch's t-test | 0.00016 (<0.05) | **Reject H₀** — Longer tweets receive significantly more likes on average |

---

## 🛠 Tools & Libraries

- **Python**  
- **Pandas / NumPy** — Data manipulation, feature engineering, and rate computation  
- **Matplotlib / Seaborn** — Scatter plots, box plots, and KDE density distributions  
- **SciPy (`stats`)** — Kruskal–Wallis, Mann–Whitney U, and Welch's t-test  
- **X API v2 / Requests** — Data extraction and JSON payload parsing

---

## 🔭 Future Research Directions

- Interaction analysis between tweet length, media type (image/video/poll), and posting time  
- Semantic embedding clustering and sentiment analysis of tweet text  
- Predictive machine learning models for tweet impression and like forecasting  
- Longitudinal tracking across broader time windows and niche topic categories

---

## 📚 References

- Kruskal, W. H., & Wallis, W. A. (1952). Use of ranks in one-criterion variance analysis. *JASA*, 47(260), 583–621.
- Mann, H. B., & Whitney, D. R. (1947). On a test of whether one of two random variables is stochastically larger than the other. *Ann. Math. Statist.*, 18, 50–60.
- Yuen, K. K. (1974). The two-sample trimmed t for unequal population variances. *Biometrika*, 61(1), 165–170.
- X API v2 Official Documentation: https://developer.x.com/en/docs/x-api

---

### Authors

- **Nguyen The Hung** 
