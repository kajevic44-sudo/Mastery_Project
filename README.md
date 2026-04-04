# Mastery_Project
Customer segmentation and reward strategy using TravelTide dataset



# **TravelTide Customer Segmentation Project**  
*Mastery Project — SQL • Python • Feature Engineering • K‑Means Segmentation*

---

##  Project Overview

This repository contains an end‑to‑end analytics project developed for the TravelTide Mastery Program. The goal is to analyze customer behavior, engineer meaningful features, segment users into actionable groups, and assign each customer a personalized reward perk to support TravelTide’s retention strategy.

The project integrates:

- SQL data extraction and cleaning  
- Python‑based feature engineering  
- K‑Means clustering  
- Behavioral interpretation  
- Business recommendations  
- Executive‑level communication  

---

##  Business Objective

TravelTide aims to improve **customer retention** by launching a personalized rewards program.  
To support this initiative, the analytics team must:

- understand how customers behave  
- identify natural behavioral segments  
- assign the most relevant perk to each user  
- provide insights that marketing can directly apply in campaigns  

This project delivers exactly that.

---

##  Repository Structure

```
traveltide-segmentation/
│
├── data/
│   ├── session_level_clean.csv
│   ├── user_level_aggregate.csv
│   ├── clusters_with_perks.csv
│   └── cluster_summary.csv
│
├── notebooks/
│   └── final_notebook.ipynb
│
├── sql/
│   └── week1_data_prep.sql
│
├── reports/
│   ├── executive_summary.pdf
│   ├── week1_report.pdf
│   ├── week2_3_report.pdf
│   └── final_report.pdf
│
├── slides/
│   └── presentation.pptx
│
└── README.md
```

---

##  Workflow Summary (Week 1–4)

### **Week 1 — SQL Exploration & Data Preparation**
- Defined cohort (8+ sessions, from 2023‑01‑05 onward)  
- Cleaned session‑level data  
- Resolved anomalies (e.g., invalid hotel nights)  
- Created session‑level and user‑level analytical tables  

### **Week 2 — Feature Engineering**
Engineered behavioral metrics including:

- `booking_rate`  
- `cancellation_rate`  
- `discount_attention_index`  
- `travel_intensity_index`  
- `sessions_booking_rate`  
- `bags_per_seat_avg`  
- `avg_session_minutes`  
- `total_bookings`

### **Week 3 — Customer Segmentation**
- StandardScaler applied to all features  
- K‑Means clustering (k = 2)  
- Silhouette analysis  
- Cluster interpretation  
- Perk assignment logic  

### **Week 4 — Communication & Reporting**
- Visualizations (bar chart, heatmap, radar chart, scatter plot)  
- Executive summary  
- Final report  
- Presentation deck  

---

##  Feature Engineering Highlights

The project focuses on creating metrics that capture:

### **Engagement**
- average session duration  
- total sessions  
- total clicks  

### **Booking Behavior**
- total bookings  
- booking rate  
- cancellation rate  

### **Discount Sensitivity**
- discount booking rate  
- discount attention index  

### **Travel Intensity**
- travel intensity index  
- bags per seat average  

These features provide a compact and expressive representation of customer behavior.

---

##  Segmentation Approach

### **Model**
- **K‑Means (k = 2)**  
- StandardScaler for normalization  
- Silhouette score used to validate separation  
- Visual confirmation via scatter plot and radar chart  

### **Cluster Profiles**

| Cluster | Behavioral Profile | Recommended Perk |
|--------|--------------------|------------------|
| **0** | Low engagement, low travel intensity, low discount sensitivity | **Convenience perks** |
| **1** | High engagement, high travel intensity, strong discount sensitivity | **Discount perks** |

---

##  Visualizations Included

- **Correlation Heatmap**  
- **Bar Chart — Key Metrics by Cluster**  
- **Radar Chart — Cluster Profiles**  
- **Scatter Plot — Cluster Separation**  
- **Elbow Method**  

All visualizations are generated in `final_notebook.ipynb`.

---

##  Perk Assignment Logic

Based on behavioral interpretation:

- **Cluster 0 → Convenience perks**  
  (priority boarding, seat selection, smoother travel experience)

- **Cluster 1 → Discount perks**  
  (vouchers, hotel coupons, promotional offers)

---

##  KPIs for Measuring Success

To evaluate the rewards program:

- repeat booking rate  
- perk redemption rate  
- revenue per active user  
- cancellation behavior  
- rewards enrollment rate  

---

##  Deliverables

- SQL extraction and cleaning workflow  
- Python segmentation pipeline  
- Engineered dataset  
- Cluster assignments  
- Executive summary  
- Week‑by‑week reports  
- Final presentation  

---

##  Project Status

The project is **fully completed** and ready for academic submission or integration into TravelTide’s marketing strategy.

