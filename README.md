# 🚚 Logistic Delay Prediction using Logistic Regression

## Project Overview
This is a **practical machine learning exercise inspired by a real logistics problem**.

Let’s be clear from the start 🙂  
The goal here is **not** to chase the highest possible metric or pretend this model will magically fix operations.  
The goal is to **learn**, to **analyze**, and to **think probabilistically** about why delivery delays happen.

Logistic Regression is used here as a **tool for understanding**, not as an end in itself.

---

## Problem Statement
Delivery delays are a recurring pain point in logistics.

They rarely come from a single cause.  
Instead, they emerge from a mix of operational factors: dock congestion, loading times, route complexity, priorities, and human experience.

Rather than treating delays as isolated failures, this project approaches them as a **probabilistic outcome influenced by process variables**.

If this sounds familiar… you’ve probably lived it.

---

## Objective 🎯
The main objectives of this project are to:

- Build a **binary classification model** to estimate the probability of delivery delay.
- Use Logistic Regression as an **interpretative model**, not just a predictive one.
- Create a **learning-oriented base** to explore how operational variables influence risk.

This project is intentionally designed as a **foundation for analysis**, not as a production-ready solution.

No magic. Just probabilities.

---

## Dataset Description 📊
The dataset represents a **realistic logistics environment**, that reflects common operational conditions found in day-to-day delivery operations.

Each row corresponds to a single shipment, described by a set of operational and contextual variables.

### Features (X)
The input variables include:

- **Distance_km**: Total route distance in kilometers.
- **Weight_kg**: Shipment weight in kilograms.
- **Number_of_stops**: Number of delivery stops along the route.
- **Shipment_priority**: Priority flag (0 = standard shipment, 1 = urgent shipment).
- **Loading_time_min**: Time required to load the shipment at the dock (minutes).
- **Dock_waiting_time_min**: Waiting time before the shipment is served at the dock (minutes).
- **Operator_experience_years**: Driver/operator experience measured in years.
- **Route_type**: Route category (`urban`, `mixed`, `long`).
- **Departure_shift**: Departure shift (`day`, `night`).

### Target Variable (Y)
- **Delay**: Delivery outcome  
  - **0 = On-time delivery**  
  - **1 = Delayed delivery**

### Data Origin (Real-World Perspective)
Each variable reflects information that typically comes from **different operational systems in a real logistics environment**:

- **Distance_km, Number_of_stops, Route_type, Departure_shift**  
  → Transportation Management System (TMS) and route planning tools.

- **Weight_kg, Shipment_priority**  
  → ERP and commercial order management systems.

- **Loading_time_min, Dock_waiting_time_min**  
  → Warehouse Management System (WMS), dock scheduling tools, or manual check-in/check-out records.

- **Operator_experience_years**  
  → HR systems or operator master data.

- **Delay (target variable)**  
  → Comparison between planned delivery times (TMS) and actual delivery timestamps, often validated through GPS and customer confirmation.

> In real-world operations, this type of dataset rarely exists in a single system.  
> It is typically built by **integrating data across multiple sources**, which is why understanding process context is just as important as modeling. 🙂

---

## Modeling Approach 🧠
A **Logistic Regression model** was selected because:

- It is transparent and interpretable
- It models **probability**, not certainty
- It forces you to think in terms of trade-offs

This model doesn’t try to be clever.  
It tries to be **honest**.

---

## Key Results 📈
Standard classification metrics are reported, but they are **not the headline**.

What really matters here is that the model allows us to:
- Identify **high-impact operational drivers**
- Visualize **probability surfaces** for key variables
- Understand how risk evolves as conditions change

Accuracy matters.  
Understanding matters more.

---

## Simulation & Scenarios 
A simple **scenario simulator** is included in the notebook.

It allows you to:
- Define hypothetical shipment conditions
- Estimate the probability of delay
- Ask “what if?” without pretending to predict the future

This is where the model becomes a **conversation tool**, not just code.

---

## Business Insights 
Some patterns become very clear:

- Dock-related variables (waiting and loading time) are major risk drivers
- Operational complexity increases uncertainty
- Experience and prioritization help absorb variability

Nothing revolutionary.  
Just quantified.

---

## Project Outputs 📂
This repository contains:
- A dataset ('.csv') with operational variables
- A Jupyter Notebook with the full analysis, simulation, and visualizations
- A PDF summary with results and conclusions for non-technical readers

---

## Next Steps 🚀
If you wanted to push this further:
- Tune decision thresholds
- Engineer additional features
- Compare with non-linear models
- Integrate into a decision-support workflow

But that’s a different conversation.

---

—
Not magic. Just probabilities.  
**Where f(x) meets Kaizen**  
LozanoLsa
Regards from MX