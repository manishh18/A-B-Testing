# A/B Testing Analysis – Booking Conversion Experiment

##  Project Overview

This project analyzes the results of an A/B test conducted by an online travel agency to evaluate the impact of a **new search ranking algorithm** on **conversion rate**. The goal is to determine whether the new variant should be rolled out fully based on its impact on:

- **Primary Metric**: Conversion rate (whether a user made a booking)
- **Guardrail Metric**: Time to booking (to ensure no negative user experience)

---

## 🗂 Datasets Used

Two datasets were used:

- `sessions_data.csv`: Contains session-level booking data.
- `users_data.csv`: Contains experiment group assignments for users.

After merging the two, we analyzed the resulting `sessions_x_users` dataset, which includes:

- `session_id`, `user_id`
- `session_start_timestamp`, `booking_timestamp`
- `conversion` (binary metric)
- `time_to_booking` (continuous metric)
- `experiment_group` (`control` or `variant`)

---

##  Key Methodology

### 1. Sample Ratio Mismatch (SRM)

We checked whether the actual group sizes matched expected proportions.

- Control: 7630 users
- Variant: 7653 users
- **SRM p-value**: 0.8524  
 **No sample ratio mismatch detected.**

---

### 2. Primary Metric: Conversion Rate

- **Statistical Test**: Two-proportion Z-test  
- **Effect Size**: Relative difference in conversion rates
- 
 **Relative Effect** = (Mean<sub>Variant</sub> / Mean<sub>Control</sub>) − 1


| Metric           | Value    |
|------------------|----------|
| p-value          | 0.0002   |
| Effect Size      | +14.22%  |
| Alpha (Significance Level) | 0.10 |

 Statistically significant improvement in conversion rate.

---

### 3. Guardrail Metric: Time to Booking

- **Statistical Test**: Two-sided T-test  
- **Effect Size**: Relative difference

| Metric           | Value    |
|------------------|----------|
| p-value          | 0.5365   |
| Effect Size      | -0.79%   |
| Alpha (Significance Level) | 0.10 |

 No statistically significant harm detected.

---

### 4. Final Decision Logic

| Metric          | Meets Criteria? |
|-----------------|------------------|
| Conversion Rate |  Significant and positive |
| Time to Booking |  Not harmed      |

###  **Final Decision: Launch the Variant**  
The experiment results are significantly positive, and the guardrail metric was not harmed. A full rollout is recommended.

---

##  Technologies Used

- Python (Pandas, NumPy, SciPy, statsmodels)
- Jupyter Notebook
- Markdown (for documentation)



