# RBA Payment Trends: Forecasting and Shift Detection

**Walsh University Capstone Project**  
Master of Science in Artificial Intelligence and Machine Learning

---

## Project Overview

This project analyses official monthly retail payment statistics published by the Reserve Bank of Australia (RBA). The main objective is to understand the ongoing shift from traditional payment methods (cash and cheques) to modern digital payments, especially the New Payments Platform (NPP).

---

## Data Description

The project uses four official RBA datasets. All files were merged on the `Date` column. Below are the selected columns used in the analysis:

### Selected Columns

| File | Original Code       | Modified Column Name              | Description |
|------|---------------------|-----------------------------------|-----------|
| C01  | CCCCSTPNSA          | `Credit_Purchases_Count`          | Number of purchases made using credit and charge cards |
| C01  | CCCCSTPVSA          | `Credit_Purchases_Value`          | Value of purchases made using credit and charge cards |
| C01  | CCCCSTTNSA          | `Total_Cards_Transactions_Count`  | Total number of card transactions |
| C01  | CCCCSTTVSA          | `Total_Cards_Transactions_Value`  | Total value of card transactions |
| C04  | CACWTNSA            | `Cash_Withdrawal_Count`           | Total number of cash withdrawals (mainly debit cards) |
| C04  | CACWTVSA            | `Cash_Withdrawal_Value`           | Total value of cash withdrawals |
| C05  | CCQCTNSA            | `Cheques_Count`                   | Total number of cheque transactions |
| C05  | CCQCTVSA            | `Cheques_Value`                   | Total value of cheque transactions |
| C06  | CCDEPNPPTNSA        | `NPP_Total_Count`                 | Total number of NPP (instant) payments |
| C06  | CCDEPNPPTVSA        | `NPP_Total_Value`                 | Total value of NPP payments |
| C06  | -                   | `Direct_Entry_Total_Count`        | Total number of direct entry payments (credit + debit transfers) |
| C06  | -                   | `Direct_Entry_Total_Value`        | Total value of direct entry payments |

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
