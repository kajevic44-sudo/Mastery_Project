## TravelTide Customer Segmentation And Perk Assignment

### Mastery Project

Author: Armin Kajevic, M.Sc.

### Project Overview

TravelTide is an e-booking startup with a retention problem: many users book once and do not return.  
The goal of this project is to assign each eligible user the single perk they are most likely to value, with the aim of improving repeat engagement and long-term retention.

The analytical workflow is intentionally split into two layers:

1. Exploratory clustering to understand broad behavioral structure.
2. Perk-affinity scoring to make the final one-per-user perk recommendation.

That distinction matters. The cluster solution is used for interpretation, while the final business decision is made by explicit scoring rules tied to the available perks.

### Business Goal

Each eligible user is assigned one of five perks:

1. Free Checked Bag
2. No Cancellation Fee
3. Exclusive Discounts
4. 1 Night Free Hotel with Flight
5. Free Hotel Meal

### Cohort Definition

The cohort includes users with:

- at least 8 sessions
- session activity on or after `2023-01-05`

This ensures each user has enough observed behavior to support meaningful profiling.

### Repository Structure

- `TravelTide_Mastery_Project.ipynb`: main notebook
- `user_features_final.csv`: older user-level export kept as reference
- `user_features_engineered_final.csv`: reproducible engineered user-level dataset used by the notebook by default
- `users_with_assigned_perks.csv`: final user-to-perk assignment output
- `perk_profiles_summary.csv`: perk-level profile summary output
- `TravelTide_Customer_Segmentation.pdf`: presentation deck
- `requirements.txt`: pinned Python dependencies for notebook execution

### Reproducibility

The notebook now runs from `user_features_engineered_final.csv` by default so the repo is executable without requiring a live database connection.

The SQL extraction path is still preserved in the notebook for full end-to-end rebuilds from the TravelTide database.

Use:

```bash
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
```

### Methodology

#### 1. Data Extraction And Cleaning

The original analytical base is built from four tables:

- `users`
- `sessions`
- `flights`
- `hotels`

Cleaning decisions in the notebook include:

- boolean standardization for modeling
- session-duration calculation from `session_start` and `session_end`
- correction of invalid hotel nights using `check_in_time` and `check_out_time`
- IQR-based clipping for selected behavioral and monetary variables

#### 2. Feature Engineering

The notebook aggregates session-level data to the user level and builds a broader behavioral feature set, including:

- `booking_rate`
- `cancellation_rate`
- `discount_booking_rate`
- `discount_attention_index`
- `travel_intensity_index`
- `bags_per_seat_avg`
- `hotel_booking_share`
- `bundle_booking_index`
- `avg_nights`

These features support both exploratory segmentation and the later perk-scoring logic.

#### 3. Exploratory Clustering

K-means is evaluated across multiple values of `k` using both inertia and silhouette score.

In the current reproducible notebook run, the best silhouette score occurs at `k = 4`.  
That clustering result is used to describe broad behavioral structure only. It is not used directly as the final perk-assignment mechanism.

#### 4. Perk Affinity Scoring

The final recommendation layer computes five perk-specific scores:

- `free_checked_bag_score`
- `no_cancellation_fee_score`
- `exclusive_discounts_score`
- `one_night_free_hotel_with_flight_score`
- `free_hotel_meal_score`

Each score is based on a weighted combination of the engineered behavioral features.  
The assigned perk is simply the highest-scoring perk for each user.

### Current Outputs

The reproducible notebook run generates:

- `user_features_engineered_final.csv`
- `users_with_assigned_perks.csv`
- `perk_profiles_summary.csv`

### Key Analytical Position

The central modeling claim in this project is:

- clustering explains the market structure
- scoring makes the business recommendation

This is the narrative used in the notebook and should also be the narrative used when presenting the project.

### Notes On Consistency

Older repo artifacts may reflect an earlier version of the project narrative, including a `k = 2` clustering interpretation.  
The notebook and this README now follow the executable, reproducible workflow in the repository.

### Contact

Armin Kajevic, M.Sc.  
Email: `armin.kajevic@outlook.de`
