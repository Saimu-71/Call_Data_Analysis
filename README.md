# 📊 Telecom Billing & Margin Optimization Dashboard (Jan–Feb–Mar)

This Power BI project provides a comprehensive telecom billing analysis for January, February, and March. It includes **client-wise and vendor-wise revenue, cost, and gross margin insights**, powered by DAX and rate simulation algorithms. This dashboard is built to assist telecom and VoIP companies in **improving profitability, optimizing billing strategies, and evaluating rate increases with real-time visual feedback**.

---

## 📁 Project Files

- **Billing_File.xlsx** – Input file containing call records, client/vendor mapping, and rate structures
- **Avoxi Data.pbix** – Main Power BI report with complete DAX logic, modeling, and dashboard views
- **Avoxi Data Analysis.xlsx** – Summary result file showing final gross margin, updated billing, and client/vendor comparisons
- **Avoxi Call Data Analysis.mp4** – Video walkthrough of the dashboard, DAX measures, and overall data model structure

---

## 📊 Dashboard Overview

- **Client View**: Revenue, cost, and margin by client
- **Vendor View**: Cost share and efficiency tracking
- **Rate Simulation**: Projected outcomes after rate increases (Mobile: 7%, Landline: 20%)
- **Revenue Target Planning**: Rate adjustment required to achieve 45% margin goal

---

## 💡 Key Visual Features

### 🔍 Filters
- Customer
- Vendor
- Call Type
- Country
- Month

### 📊 KPI Cards
- Total Revenue
- Total Cost
- Gross Margin (%)
- Revenue Gap to 45% Margin
- Required Revenue to Reach Target
- Rate Increase % (Landline/Mobile)

### 📊 Visualizations
- Gross Margin % by Country, Vendor, Client
- Cost Distribution by Vendor
- Billing Distribution (Pre/Post Simulation)
- Revenue Share vs Volume Share
- Simulated Client Billing Breakdown

---

## 🤷️ DAX Calculations & Logic

### 📅 Base Measures:
```DAX
Total_Revenue = SUMX(CallData, CallData[Duration_Minutes] * CallData[Client_Rate])
Total_Cost = SUMX(CallData, CallData[Payable_Minutes] * CallData[Carrier_Rate])
Gross_Margin = [Total_Revenue] - [Total_Cost]
Gross_Margin_% = DIVIDE([Gross_Margin], [Total_Revenue])
```

### ✅ Rate Simulation Logic:
```DAX
Updated_Client_Rate =
SWITCH(TRUE(),
    CallData[Call_Type] = "Mobile", CallData[Client_Rate] * 1.07,
    CallData[Call_Type] = "Landline", CallData[Client_Rate] * 1.20,
    CallData[Client_Rate]
)

Updated_Revenue = SUMX(CallData, CallData[Duration_Minutes] * [Updated_Client_Rate])
Updated_Gross_Margin = [Updated_Revenue] - [Total_Cost]
Updated_Gross_Margin_% = DIVIDE([Updated_Gross_Margin], [Updated_Revenue])
```

### 💰 Target Calculation Logic:
```DAX
Required_Revenue_45 = [Total_Cost] / (1 - 0.45)
Revenue_Gap_45 = [Required_Revenue_45] - [Total_Revenue]
Client_Rate_Increase_% = DIVIDE([Required_Revenue_45], [Total_Revenue]) - 1
```

---

## 📈 Example Results Snapshot

### 📌 Billing by Client (Pre vs Post Rate Change)
| Client     | Bill by Client | Updated Bill | Revenue % | Updated % |
|------------|----------------|---------------|------------|------------|
| Client 1   | $2,288.63      | $2,584.75     | 2.71%      | 2.71%      |
| Client 4   | $18,095.18     | $20,431.43    | 21.40%     | 21.45%     |

### 📌 Cost by Vendor
| Vendor ID | Total Cost | Cost % |
|-----------|------------|--------|
| Vendor 1  | $18,487.05 | 36.20% |
| Vendor 4  | $19,275.99 | 37.74% |

### 📌 Gross Margin by Vendor
| Vendor ID | Avg Margin % | Updated Margin % |
|-----------|---------------|------------------|
| Vendor 1  | 51.23%        | 57.51%           |
| Vendor 4  | 46.87%        | 53.68%           |

---

## 🚀 Business Impact

- ✅ Identified top and bottom-performing clients and vendors
- ✅ Modeled rate changes to achieve target margins
- ✅ Pinpointed vendors causing excessive cost drains
- ✅ Proposed rate changes by call type to improve profit

---

## 👩‍💼 Use Cases

This dashboard is perfect for:
- Telecom or VoIP operations teams
- Financial analysts in carrier billing
- Strategy and pricing teams
- MSPs and call routing vendors looking to maximize margins

---

## 💮 Insights Delivered

- Strategic view of client profitability
- Vendor efficiency and cost behavior
- Easy comparison of billing before/after rate change
- Data-driven pricing decisions to maintain 45%+ gross margin

---

## 📄 How to Use

1. Open **Avoxi Data.pbix** in Power BI Desktop
2. Refresh the data using **Billing_File.xlsx**
3. Review simulation outcomes in **Avoxi Data Analysis.xlsx**
4. Watch **Avoxi Call Data Analysis.mp4** for full walkthrough

---

## 🏆 Final Notes

This project showcases advanced Power BI techniques with real business logic, financial simulation, and actionable visual storytelling. Ideal for companies aiming to transform raw telecom data into margin-driven insights and strategic decisions.

> For questions or collaboration: **[saimutanshen@gmail.com](mailto:saimutanshen@gmail.com)**

