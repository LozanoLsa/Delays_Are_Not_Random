# Delays Are Not Random — Logistic Regression

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LozanoLsa/Delays_Are_Not_Random/blob/main/01_Logistic_Regression_Logistics.ipynb)

> *"A delay is not just a late shipment — it's a break in the operational flow. And breaks in operational flow always leave traces in the data."*

---

## 🎯 Business Problem

Every logistics operation deals with delays. The typical response is reactive: track the KPI, escalate when it's red, firefight until it's green again. This project asks a different question — what if you could score each shipment's probability of being late **before it leaves the dock**?

With 67.8% of shipments arriving delayed in this dataset, the problem isn't rare. It's structural. And structural problems have structural signals — which is exactly what Logistic Regression is built to find.

---

## 📊 Dataset

- **1,500 shipment records** from logistics operation
- **Target:** `Reached.on.Time` (binary) — 0 = delayed, 1 = on time
- **Class balance:** 67.8% delayed (imbalanced toward the problem class)
- **Source:** Simulated ERP/TMS data reflecting real logistics feature distributions

| Feature | Type | Description |
|---------|------|-------------|
| `Warehouse_block` | Categorical | Storage zone (A–F) |
| `Mode_of_Shipment` | Categorical | Ship / Flight / Road |
| `Customer_care_calls` | Numerical | Support interactions before delivery |
| `Customer_rating` | Ordinal | 1–5 satisfaction score |
| `Cost_of_the_Product` | Numerical | USD product value |
| `Prior_purchases` | Numerical | Customer purchase history |
| `Product_importance` | Categorical | Low / Medium / High |
| `Gender` | Categorical | Customer demographic |
| `Discount_offered` | Numerical | % discount applied |
| `Weight_in_gms` | Numerical | Shipment weight |

**Surprising EDA finding:** Ship mode has the highest delay rate (69.2%) — counterintuitive until you account for volume and route complexity.

---

## 🤖 Model

**Algorithm:** Logistic Regression — `sklearn.linear_model.LogisticRegression`

The choice is deliberate. Before reaching for a complex ensemble, the right question is: *can a simple, interpretable model explain this problem well enough to act on?* In logistics, a model that operations teams can read and trust beats a black-box with 2% higher accuracy every time.

Logistic Regression outputs delay probability (0–1), not just binary pass/fail — enabling risk-based prioritization across the shipment queue.

**Preprocessing:** StandardScaler on numerics, Label Encoding for categoricals, all inside a sklearn Pipeline.

---

## 📈 Key Results

| Metric | Value |
|--------|-------|
| Accuracy | 67.3% |
| Precision (Delay) | 75.8% |
| Recall (Delay) | 81.4% |
| F1 (Delay) | 0.785 |

**Why Recall matters here:** Missing a delay costs more than a false alarm. 81.4% recall means the model catches 4 out of 5 actual delays before they happen.

---

## 🔍 Top Delay Drivers (Log-Odds Coefficients)

| Feature | Coefficient | Direction |
|---------|-------------|-----------|
| `Customer_care_calls` | +0.82 | 🔴 Risk factor |
| `Discount_offered` | +0.67 | 🔴 Risk factor |
| `Prior_purchases` | −0.54 | 🔵 Protective |
| `Cost_of_the_Product` | −0.41 | 🔵 Protective |

More customer care calls = more likely delayed. Loyal customers (high prior purchases) see fewer delays. High-value products get handled more carefully. These aren't surprises — they're quantified.

---

## 🗂️ Repository Structure

```
Delays_Are_Not_Random/
├── 01_Logistic_Regression_Logistics.ipynb  # Notebook (no outputs)
├── logistics_shipments_data.csv            # Sample dataset (250 rows)
├── README.md
└── requirements.txt
```

> 📦 **Full Project Pack** — complete dataset (1,500 rows), notebook with full outputs, presentation deck (PPTX + PDF), and `app.py` simulator available on [Gumroad](https://lozanolsa.gumroad.com).

---

## 🚀 How to Run

**Option 1 — Google Colab:** Click the badge above.

**Option 2 — Local:**
```bash
pip install -r requirements.txt
jupyter notebook 01_Logistic_Regression_Logistics.ipynb
```

---

## 💡 Key Learnings

1. **Coefficients are storytelling tools** — they translate model output into language operations managers actually understand.
2. **Recall > Accuracy in logistics** — with 67.8% base delay rate, a naive classifier scores 67% accuracy doing nothing. Recall on the delay class is the real signal.
3. **Customer care calls are a proxy for frustration** — high call volume before delivery is the model's strongest feature, and it makes operational sense.
4. **Simple models deployed beat complex models in notebooks** — Logistic Regression is often good enough, and always explainable.
5. **EDA validates model logic** — if the most important features don't make physical sense, the model is learning noise. Here they do.

---

## 👤 Author

**Luis Lozano** | Operational Excellence Manager · Master Black Belt · Machine Learning  
GitHub: [LozanoLsa](https://github.com/LozanoLsa) · Gumroad: [lozanolsa.gumroad.com](https://lozanolsa.gumroad.com)

*Turning Operations into Predictive Systems — Clone it. Fork it. Improve it.*
