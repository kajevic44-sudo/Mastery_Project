TravelTide Customer Segmentation & Perk Assignment
Mastery Project — Masterschool of Technology
Author: Armin Kajevic, M.Sc.

Project Overview
TravelTide, an e-booking startup, faces a critical retention challenge: users book once and do not return. The objective of this project is to design and implement a personalized rewards program that assigns each customer the perk they are most likely to value, thereby driving long-term retention.

This repository contains the complete end-to-end analytical pipeline, from SQL data extraction and cleaning to Python-based feature engineering, K-Means clustering, and final perk assignment scoring.

Business Goal
To assign one of five distinct perks to each eligible user based on their historical behavior:
1	Free Checked Bag
2	No Cancellation Fee
3	Exclusive Discounts
4	1 Night Free Hotel with Flight
5	Free Hotel Meal

Cohort Definition
The analysis focuses on a specific cohort of users to ensure sufficient behavioral history:
•	Minimum 8 sessions per user.
•	Recent activity: Sessions occurring from January 5, 2023 onward.

Repository Structure

├── TravelTide_Segmentation.ipynb   # Main Jupyter Notebook containing all Python analysis
├── README.md                       # Project documentation
(Note: The raw CSV data files and SQL extraction scripts are maintained separately in the database environment and are not included in this public repository for privacy reasons.)

Methodology
1. Data Extraction & Cleaning (SQL & Python)
The foundation of the analysis is built on four core tables (users, sessions, flights, hotels) joined at the session level. Data cleaning steps included:
•	Converting boolean columns to integers for modeling.
•	Computing session duration and handling anomalies (e.g., clipping negative durations).
•	Correcting invalid hotel nights using check-in and check-out timestamps.
•	Applying IQR winsorization to handle extreme outliers in numerical fields.

2. Feature Engineering
Raw session data was aggregated to the user level to create eight behavioral metrics that capture what drives perk preference:
•	booking_rate: How often sessions convert into bookings.
•	cancellation_rate: Affinity for flexibility and cancellation protection.
•	discount_attention_index: Discount exposure and responsiveness.
•	travel_intensity_index: How frequently the user travels relative to tenure.
•	bags_per_seat_avg: Luggage behavior, acting as a proxy for Free Checked Bag affinity.
•	hotel_booking_share: Hotel-heavy versus flight-heavy user preference.
•	bundle_booking_index: Tendency to book complete travel packages.

3. Exploratory Clustering
K-Means clustering was applied to the scaled behavioral metrics. Both the Elbow Method and Silhouette Score indicated that k=2 provided the best mathematical separation of users, revealing two broad behavioral groups:
•	Cluster 0 (Stable Travellers): Higher booking rates, strong preference for hotels, and a tendency to book flight+hotel bundles.
•	Cluster 1 (Active Explorers): Higher cancellation rates, highly responsive to discounts, and more page clicks per session.

4. Perk Affinity Scoring
While k=2 is statistically optimal, it is insufficient to effectively assign five distinct perks. Therefore, a granular scoring approach was implemented. Each user received an affinity score for each of the five perks based on a weighted combination of their behavioral metrics. The perk with the highest score was assigned to the user.

Key Findings & Recommendations
•	Data-Driven Assignment: The affinity scoring model successfully distributed the five perks across the cohort, ensuring that each user received a relevant reward based on their specific behavior.
•	Next Steps: Launch an A/B test by rolling out the assigned perks to 80% of the cohort, keeping 20% as a control group to measure true incremental lift.
•	KPIs to Monitor: Retention Rate, Perk Redemption Rate, and Incremental Revenue per User.

Contact
For any questions regarding this analysis, please contact:
•	Armin Kajevic, M.Sc.
•	Email: armin.kajevic@outlook.de
•	Phone: 01731885542

