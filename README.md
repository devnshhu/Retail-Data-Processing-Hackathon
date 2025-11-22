🧠 Model Description

Our dataset is provided in CSV format, containing customer transactions such as Invoice Date, Quantity, Unit Price, and Customer ID. After cleaning and aggregating this data into customer-level features (Recency, Frequency, Monetary value, and Loyalty Point Balance), we apply a Gradient Boosting Model to classify customers into two target segments required by the Loyalty Lens use case:

High-Spender (Top 10% by Monetary Value)

At-Risk Customer (No purchases in 30+ days + positive point balance)

🔍 What the Model Does

After computing RFM metrics and loyalty points, the model uses Gradient Boosting Classification (XGBoost-style logic) to predict the probability that a customer belongs to:

High-Spender segment

At-Risk segment

This model learns the patterns from customer behavior:

Recency (how long since last purchase)

Frequency (how often they buy)

Monetary (how much they spend)

Point Balance (unused loyalty points)

Optional: average order value trend, product diversity

🚀 Why Gradient Boosting?

We deliberately use a Boosting Model (instead of logistic regression or a neural network) because:

It handles small to medium tabular datasets extremely well

It automatically captures non-linear interactions (e.g., high spenders who are also infrequent buyers)

It requires minimal feature engineering, ideal under hackathon time constraints

It is interpretable — feature importance can clearly show:

Monetary spend impact

Recency importance

Point balance effect on churn risk

This makes the approach both accurate and explainable, which is critical for loyalty analytics.

📦 Final Output of the Model

The model generates:

High-Spender Probability (0–1)

At-Risk Probability (0–1)

A final Segment Label:

"High-Spender"

"At-Risk"

"Regular"

