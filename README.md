# RBA Payment Trends: Forecasting and Shift Detection

**Walsh University Capstone Project**  
Master of Science in Artificial Intelligence and Machine Learning

---

## Project Overview

This project analyses official monthly retail payment statistics published by the Reserve Bank of Australia (RBA). The main objective is to understand the ongoing shift from traditional payment methods (cash and cheques) to modern digital payments, especially the New Payments Platform (NPP).

---

### 📌 Notebook viewing 
GitHub sometimes fails to render large Jupyter notebooks. If the notebook doesn’t load, please open it using the nbviewer link provided in the report.

---

## Data Description

The project uses four official RBA datasets. All files were merged on the `Date` column. Below are the selected columns and the feature Engineered columns used in the analysis:

### Selected Columns

### Data Dictionary

| S.no | Variable Name                        | Definition                                                      | Datatype   | Range / Values                  | Missing Values Handling                  | Notes / Source                  |
|------|--------------------------------------|-----------------------------------------------------------------|------------|---------------------------------|------------------------------------------|---------------------------------|
| 1    | Date                                 | Monthly reporting period                                        | Datetime   | 2018-01 to 2026-02              | None (after initial filter)              | Common index                    |
| 2    | CCCCSTPNSA                           | Credit Purchases Count (Scaled)                                 | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C01)              |
| 3    | CCCCSTPVSA                           | Credit Purchases Value in millions (Scaled)                     | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C01)              |
| 4    | CCCCSTTNSA                           | Total Cards Transactions Count (Scaled)                         | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C01)              |
| 5    | CCCCSTTVSA                           | Total Cards Transactions Value in millions (Scaled)             | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C01)              |
| 6    | CACWTNSA                             | Cash Withdrawal Count (Scaled)                                  | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C04)              |
| 7    | CACWTVSA                             | Cash Withdrawal Value in millions (Scaled)                      | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C04)              |
| 8    | CCQCTNSA                             | Cheques Total Count (Scaled)                                    | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C05)              |
| 9    | CCQCTVSA                             | Cheques Total Value in millions (Scaled)                        | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C05)              |
| 10   | CCDEPNPPTNSA                         | NPP Total Count (Scaled)                                        | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C06)              |
| 11   | CCDEPNPPTVSA                         | NPP Total Value in millions (Scaled)                            | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C06)              |
| 12   | CCDEPDEPTNSA                         | Direct Entry Total Count (Scaled)                               | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C06)              |
| 13   | CCDEPDEPTVSA                         | Direct Entry Total Value in millions (Scaled)                   | float64    | [0, 1]                          | None (after scaling)                     | Original (RBA C06)              |
| 14   | Year                                 | Year of the reporting period                                    | int32      | 2018-2026                       | None                                     | Engineered feature              |
| 15   | Month                                | Month of the reporting period (1-12)                            | int32      | 1-12                            | None                                     | Engineered feature              |
| 16   | Quarter                              | Quarter of the reporting period (1-4)                           | int32      | 1-4                             | None                                     | Engineered feature              |
| 17   | DayOfWeek                            | Day of the week for the last day of the month (0=Mon, 6=Sun)    | int32      | 0-6                             | None                                     | Engineered feature              |
| 18   | DayOfYear                            | Day of the year for the last day of the month (1-366)           | int32      | 1-366                           | None                                     | Engineered feature              |
| 19   | CCCCSTPVSA_roll_3m                   | 3-month rolling mean of Credit Purchases Value (Scaled)         | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 20   | CACWTVSA_roll_3m                     | 3-month rolling mean of Cash Withdrawal Value (Scaled)          | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 21   | CCQCTVSA_roll_3m                     | 3-month rolling mean of Cheques Total Value (Scaled)            | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 22   | CCDEPNPPTVSA_roll_3m                 | 3-month rolling mean of NPP Total Value (Scaled)                | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 23   | CCDEPDEPTVSA_roll_3m                 | 3-month rolling mean of Direct Entry Total Value (Scaled)       | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 24   | CCCCSTPVSA_roll_6m                   | 6-month rolling mean of Credit Purchases Value (Scaled)         | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 25   | CACWTVSA_roll_6m                     | 6-month rolling mean of Cash Withdrawal Value (Scaled)          | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 26   | CCQCTVSA_roll_6m                     | 6-month rolling mean of Cheques Total Value (Scaled)            | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 27   | CCDEPNPPTVSA_roll_6m                 | 6-month rolling mean of NPP Total Value (Scaled)                | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 28   | CCDEPDEPTVSA_roll_6m                 | 6-month rolling mean of Direct Entry Total Value (Scaled)       | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 29   | Total_Payments                       | Sum of all scaled transaction counts                            | float64    | [0, 5] (approx)                 | None                                     | Engineered feature              |
| 30   | Cards_Share_Percent                  | Cards transaction count as a percentage of Total_Payments       | float64    | [0, 100]                        | None                                     | Engineered feature              |
| 31   | Cash_Share_Percent                   | Cash withdrawal count as a percentage of Total_Payments         | float64    | [0, 100]                        | None                                     | Engineered feature              |
| 32   | Cheques_Share_Percent                | Cheques count as a percentage of Total_Payments                 | float64    | [0, 100]                        | None                                     | Engineered feature              |
| 33   | NPP_Share_Percent                    | NPP transaction count as a percentage of Total_Payments         | float64    | [0, 100]                        | None                                     | Engineered feature              |
| 34   | DirectEntry_Share_Percent            | Direct Entry transaction count as a percentage of Total_Payments| float64    | [0, 100]                        | None                                     | Engineered feature              |
| 35   | CCCCSTPVSA_MoM_Growth                | Month-on-Month percentage growth of Credit Purchases Value      | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 36   | CACWTVSA_MoM_Growth                  | Month-on-Month percentage growth of Cash Withdrawal Value       | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 37   | CCQCTVSA_MoM_Growth                  | Month-on-Month percentage growth of Cheques Total Value         | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 38   | CCDEPNPPTVSA_MoM_Growth              | Month-on-Month percentage growth of NPP Total Value             | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 39   | CCDEPDEPTVSA_MoM_Growth              | Month-on-Month percentage growth of Direct Entry Total Value    | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 40   | CCDEPNPPTNSA_lag1                    | NPP Total Count lagged by 1 month (Scaled)                      | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 41   | CCDEPNPPTNSA_lag2                    | NPP Total Count lagged by 2 months (Scaled)                     | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 42   | CCDEPNPPTNSA_lag3                    | NPP Total Count lagged by 3 months (Scaled)                     | float64    | [0, 1]                          | Initial NaNs dropped                     | Engineered feature              |
| 43   | Cash_MoM_Growth                      | Month-on-Month percentage growth of Cash Withdrawal Count       | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 44   | Cheques_MoM_Growth                   | Month-on-Month percentage growth of Cheques Total Count         | float64    | Real numbers (can be negative)  | Initial NaN handled by dropna()          | Engineered feature              |
| 45   | Credit_Avg_Transaction_Value         | Average transaction value for credit purchases (Scaled)         | float64    | [0, 1]                          | NaNs filled with 0                       | Engineered feature              |
| 46   | NPP_Avg_Transaction_Value            | Average transaction value for NPP payments (Scaled)             | float64    | [0, 1]                          | NaNs filled with 0                       | Engineered feature              |
| 47   | NPP_vs_Cash_Shift_Interaction        | Interaction term: NPP MoM Growth * (-Cash MoM Growth)           | float64    | Real numbers                    | NaNs filled with 0                       | Engineered feature              |
---

## Key Focus Areas

- Growth of **NPP (Instant Payments)**
- Performance of **Credit and Debit Cards**
- Decline in **Cash Withdrawals** and **Cheques**
- Comparison between modern digital payments vs traditional methods

---

## Technologies Used

- Python, Pandas, NumPy
- Matplotlib & Seaborn (Visualization)
- Scikit-learn, XGBoost
- TensorFlow/Keras (LSTM Autoencoder)

---
