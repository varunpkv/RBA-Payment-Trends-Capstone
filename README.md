# RBA Payment Trends: Forecasting and Shift Detection

**Capstone Project**  
Master of Science in Artificial Intelligence and Machine Learning  
Walsh University

---

## Project Overview

This project analyses official monthly retail payment statistics published by the Reserve Bank of Australia (RBA). The main objectives are:

- To forecast the growth of NPP (instant payments) versus traditional payment methods (cash and cheques).
- To detect unexpected shifts or changes in payment behaviour over time.

---

## Data Description

The project uses four official RBA datasets. All files were merged on the **Date** column to create one clean monthly dataframe.

### 1. C6 - NPP & Direct Entry Payments
**File:** `C6-Monthly-payment-trends.xlsx`  
**Description:** Contains data on New Payments Platform (instant payments) and Direct Entry transactions.

**Selected Columns:**
- `Date` — Monthly observation date
- `NPP_Total_Txns_NSA` — Total number of NPP transactions (Not Seasonally Adjusted)
- `NPP_Total_Txns_SA` — Total number of NPP transactions (Seasonally Adjusted)
- `Cards_Total_Txns_NSA` — Total number of card transactions (Not Seasonally Adjusted)
- `Cards_Total_Txns_SA` — Total number of card transactions (Seasonally Adjusted)

### 2. C1 - Credit & Charge Cards
**File:** `C1-Cards.xlsx`  
**Description:** Detailed statistics on credit and charge card activity.

**Selected Columns:**
- `Date` — Monthly observation date
- `Credit_Cards_Active_Accounts_NSA` — Number of active credit and charge card accounts
- `Credit_Cards_Purchases_Count_NSA` — Number of purchases using credit/charge cards
- `Credit_Cards_Purchases_Value_SA` — Value of purchases using credit/charge cards (Seasonally Adjusted)
- `Total_Cards_Txns_Count_NSA` — Total number of card transactions
- `Total_Cards_Txns_Value_SA` — Total value of card transactions (Seasonally Adjusted)

### 3. C4 - ATM Cash Withdrawals
**File:** `C4-Cash-Withdrawals.xlsx`  
**Description:** Statistics on cash withdrawals from ATMs.

**Selected Columns:**
- `Date` — Monthly observation date
- `Cash_Total_Txns_NSA` — Total number of ATM cash withdrawals
- `Cash_Total_Value_SA` — Total value of ATM cash withdrawals (Seasonally Adjusted)
- `Cash_FI_Txns_NSA` — Cash withdrawals from Financial Institutions
- `Cash_Other_Txns_NSA` — Cash withdrawals from Other providers
- `Cash_CreditCard_Txns_NSA` — Cash withdrawals using Credit Cards

### 4. C5 - Cheques
**File:** `C5-Cheques.xlsx`  
**Description:** Statistics on cheque transactions.

**Selected Columns:**
- `Date` — Monthly observation date
- `Cheques_Total_Txns_NSA` — Total number of cheque transactions
- `Cheques_Total_Value_SA` — Total value of cheque transactions (Seasonally Adjusted)
- `Cheques_Processed_Txns_NSA` — Number of cheques processed by banks
- `Cheques_Processed_Value_SA` — Value of cheques processed by banks

---

## Notebooks

- `Walsh_Capstone.ipynb` — Main analysis notebook (data cleaning, EDA, modeling)

---

## Technologies Used

- Python, Pandas, NumPy
- Scikit-learn, XGBoost
- TensorFlow / Keras (LSTM Autoencoder)
- Matplotlib & Seaborn (visualization)

---
