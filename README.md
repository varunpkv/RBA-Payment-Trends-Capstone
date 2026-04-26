# RBA Payment Trends: Forecasting and Shift Detection

Capstone Project for Master of Science in Artificial Intelligence and Machine Learning (Walsh University).

## Project Overview
This project analyses official monthly retail payment statistics published by the Reserve Bank of Australia (RBA) to understand the shift from traditional payments (cash and cheques) to digital payments (especially NPP).

## Data Description

The project uses four official RBA datasets. All files were merged on the `Date` column to create one clean monthly dataframe.

### 1. C6 - NPP & Direct Entry Payments
- **NPP_Total_Txns_NSA**: Total number of NPP (instant) payments (raw)
- **NPP_Total_Txns_SA**: Total number of NPP payments (seasonally adjusted)
- **Cards_Total_Txns_NSA**: Total card transactions (raw)
- **Cards_Total_Txns_SA**: Total card transactions (seasonally adjusted)

### 2. C1 - Credit & Charge Cards
- **Credit_Cards_Active_Accounts_NSA**: Number of active credit/charge card accounts
- **Credit_Cards_Purchases_Count_NSA**: Number of purchases using credit/charge cards
- **Credit_Cards_Purchases_Value_SA**: Value of purchases (seasonally adjusted)
- **Total_Cards_Txns_Count_NSA**: Total card transactions count
- **Total_Cards_Txns_Value_SA**: Total card transaction value (seasonally adjusted)

### 3. C4 - ATM Cash Withdrawals
- **Cash_Total_Txns_NSA**: Total number of ATM cash withdrawals
- **Cash_Total_Value_SA**: Total value of ATM cash withdrawals (seasonally adjusted)
- **Cash_FI_Txns_NSA**: Cash withdrawals from bank ATMs
- **Cash_Other_Txns_NSA**: Cash withdrawals from other ATMs

### 4. C5 - Cheques
- **Cheques_Total_Txns_NSA**: Total number of cheque transactions
- **Cheques_Total_Value_SA**: Total value of cheque transactions (seasonally adjusted)

All data is publicly available from the RBA website. The final merged dataset contains approximately 122 monthly observations (last 10 years).

## Notebooks
- `Walsh_Capstone.ipynb` → Main analysis notebook
