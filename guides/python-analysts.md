---
layout: page
title: "Guide: Python for Analysts"
subtitle: "pandas, statsmodels, and sklearn tips for AI-assisted workflows"
permalink: /guides/python-analysts/
---

## Who this guide is for

This guide covers the Python tools you'll use in INFO 4340. It's not a full Python course, but rather a reference for the specific operations you need as an analyst working with AI tools. Bookmark it and come back throughout the quarter.

If you're new to Python, start with the [developer setup guide]({{ site.baseurl }}/guides/dev-setup/) to get your environment working first.

## pandas: data loading, cleaning, and analysis

pandas is the workhorse of data analysis in Python. You'll use it in every class from Week 3 onward.

### Loading data

```python
import pandas as pd

# CSV
df = pd.read_csv("data.csv")

# With options
df = pd.read_csv("data.csv", parse_dates=["date_col"], dtype={"id": str})

# Excel
df = pd.read_excel("data.xlsx", sheet_name="Sheet1")

# From a URL
df = pd.read_csv("https://example.com/data.csv")
```

### First look at your data

Run these every time you load a new dataset before asking AI anything about it.

```python
df.shape              # (rows, columns)
df.head()             # first 5 rows
df.info()             # column types and missing values
df.describe()         # summary statistics for numeric columns
df.columns.tolist()   # column names
df.dtypes             # data types
```

### Handling missing values

```python
# Count missing values per column
df.isnull().sum()

# Drop rows with any missing values (use cautiously!!!)
df_clean = df.dropna()

# Fill missing values
df["discount"] = df["discount"].fillna(0)          # fill with a value (use cautiously!!!)
df["score"] = df["score"].fillna(df["score"].mean()) # fill with mean (use cautiously!!!)

# Check: how many rows did you lose?
print(f"Before: {len(df)}, After: {len(df_clean)}, Dropped: {len(df) - len(df_clean)}")
```

### Standardizing text columns

A common data quality issue and one AI often misses.

```python
# Standardize casing
df["category"] = df["category"].str.strip().str.title()

# Check unique values
df["category"].value_counts()

# Replace specific values
df["status"] = df["status"].replace({"shipped": "Shipped", "SHIPPED": "Shipped"})
```

### Filtering

```python
# Single condition
delivered = df[df["status"] == "Delivered"]

# Multiple conditions (use & for AND, | for OR, wrap each in parentheses)
large_delivered = df[(df["status"] == "Delivered") & (df["amount"] > 1000)]

# Not equal
non_cancelled = df[df["status"] != "Cancelled"]
```

### Grouping and aggregation

```python
# Group by one column
segment_totals = df.groupby("segment")["revenue"].sum()

# Group by multiple columns
monthly_segment = df.groupby(["month", "segment"])["revenue"].sum()

# Multiple aggregations
summary = df.groupby("segment").agg(
    total_revenue=("revenue", "sum"),
    avg_revenue=("revenue", "mean"),
    order_count=("order_id", "nunique"),
    avg_discount=("discount", "mean"),
).round(2)
```

### Date operations

```python
# Parse dates (handles mixed formats)
df["date"] = pd.to_datetime(df["date"], format="mixed")

# Extract parts
df["month"] = df["date"].dt.month
df["year"] = df["date"].dt.year
df["day_of_week"] = df["date"].dt.day_name()
df["period"] = df["date"].dt.to_period("M")  # monthly period

# Date math
df["days_since"] = (pd.Timestamp.now() - df["date"]).dt.days
```

### Merging and joining

```python
# Left join (keep all rows from left, match from right)
# Default is INNER if not defined
merged = pd.merge(orders, customers, on="customer_id", how="left")

# ALWAYS check row counts after merging
print(f"Orders: {len(orders)}, Customers: {len(customers)}, Merged: {len(merged)}")
assert len(merged) == len(orders), "Merge created unexpected rows - check for duplicates"
```

### Removing duplicates

```python
# Find duplicates
print(f"Duplicate rows: {df.duplicated().sum()}")

# Remove duplicates
df_clean = df.drop_duplicates()

# Remove duplicates on specific columns
df_clean = df.drop_duplicates(subset=["order_id"])
```

## Verification checks (assertions)

From Week 4 onward, add these to every notebook. They take seconds to write and save hours of debugging.

```python
# After loading
assert len(df) > 0, "DataFrame is empty"
assert "order_id" in df.columns, "Missing expected column"

# After cleaning
assert df["date"].notna().all(), "Some dates failed to parse"
assert df["price"].min() > 0, f"Suspicious price: {df['price'].min()}"
assert df.duplicated().sum() == 0, "Duplicates still present"
assert df["segment"].nunique() == 4, f"Expected 4 segments, got {df['segment'].nunique()}"

# After filtering
assert len(delivered) < len(df), "Filter didn't remove any rows"
```

## Visualization essentials

```python
import matplotlib.pyplot as plt

# Bar chart
df.groupby("segment")["revenue"].sum().plot(kind="bar", figsize=(8, 4))
plt.title("Revenue by Segment")
plt.ylabel("Revenue ($)")
plt.tight_layout()
plt.savefig("revenue_by_segment.png", dpi=150)
plt.show()

# Line chart
monthly.plot(kind="line", figsize=(10, 4))
plt.title("Monthly Revenue Trend")
plt.tight_layout()
plt.show()

# Scatter
plt.scatter(df["discount"], df["order_total"], alpha=0.5)
plt.xlabel("Discount %")
plt.ylabel("Order Total")
plt.title("Discount vs. Order Total")
plt.show()
```

## sklearn: machine learning essentials

Used in Weeks 5-7 for clustering, classification, and evaluation.

### K-means clustering (Week 5)

```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

# Scale features first (k-means is sensitive to scale)
scaler = StandardScaler()
X_scaled = scaler.fit_transform(df[["recency", "frequency", "monetary"]])

# Fit k-means
km = KMeans(n_clusters=3, random_state=42, n_init=10)
df["cluster"] = km.fit_predict(X_scaled)

# Evaluate
sil = silhouette_score(X_scaled, df["cluster"])
print(f"Silhouette score: {sil:.3f}")  # > 0.3 is decent
```

### Text classification (Week 6)

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression

# Vectorize text
vectorizer = TfidfVectorizer(max_features=200, stop_words="english")
X = vectorizer.fit_transform(texts)

# Train classifier
clf = LogisticRegression(max_iter=1000, random_state=42)
clf.fit(X_train, y_train)
predictions = clf.predict(X_test)
```

### Evaluation metrics (Weeks 7–8)

```python
from sklearn.metrics import (
    classification_report,
    confusion_matrix,
    cohen_kappa_score,
    precision_recall_fscore_support,
)

# Full classification report
print(classification_report(y_true, y_pred))

# Cohen's kappa (inter-rater reliability)
kappa = cohen_kappa_score(rater_1, rater_2)

# Per-group precision/recall
p, r, f1, support = precision_recall_fscore_support(y_true, y_pred, labels=labels)
```

## statsmodels: linear mixed models (Week 5 alternative)

```python
import statsmodels.formula.api as smf

# Random intercept model
model = smf.mixedlm(
    "order_total ~ discount_pct + quantity",
    data=df,
    groups=df["customer_id"],
).fit()

print(model.summary())
```

## networkx: network analysis (Week 6)

```python
import networkx as nx

# Build a graph
G = nx.Graph()
G.add_edge("billing", "support", weight=3)
G.add_edge("technical", "product", weight=2)

# Centrality
degree_cent = nx.degree_centrality(G)
betweenness = nx.betweenness_centrality(G)

# Community detection
from networkx.algorithms.community import greedy_modularity_communities
communities = list(greedy_modularity_communities(G))
```

## Working with the Anthropic API

```python
import anthropic

client = anthropic.Anthropic(api_key="your-key")

response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=500,
    temperature=0,
    messages=[{"role": "user", "content": "Your prompt here"}]
)

text = response.content[0].text
```

## Tips for using AI with Python

- **Show AI your data first.** Paste `df.head(10).to_string()` and `df.info()` into your prompt so AI knows what it's working with.
- **Run each step separately.** Don't paste a 50-line AI-generated script and run it all at once. Run line by line and check intermediate outputs.
- **Add assertions after every AI-generated block.** AI doesn't verify its own code. That's your job!
- **Check the pandas version.** AI sometimes suggests deprecated syntax. If something doesn't work, check the docs.
- **Don't blindly accept `.dropna()`.** AI loves to drop missing values. Always ask: how many rows did I just lose, and should those rows have been dropped?
