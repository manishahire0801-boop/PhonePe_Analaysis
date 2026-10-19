# 💜 PhonePe Payment Insights: Powering Bharat's Digital Transactions Dashboard

A dynamic, interactive Power BI dashboard built to explore digital payment behaviour, focusing on transaction trends, payment success, customer age segments, service-wise revenue, and weekday vs weekend usage.
[
![Dashboard Preview](dashboard.png)](https://github.com/manishahire0801-boop/PhonePe_Analaysis/blob/main/PhonePe_Analysis_dashboard.png)

---

## 📌 Short Description / Purpose

The **PhonePe Payment Insights Dashboard** is an analytical Power BI report that explores **300K transactions worth ₹3.47 billion** made by **108K unique users** over 12 months. It highlights key payment metrics such as transaction volume, value, success rate, month-over-month growth, top services and top customers.

This tool is intended for **fintech analysts, product managers, marketing teams and business strategists** who want to understand how, when and why customers use digital payment services.

---

## 🛠️ Tech Stack

The dashboard was built using the following tools and technologies:

- 📊 **Power BI Desktop**: main platform used to build the report.
- 📂 **Power Query**: loading, cleaning and transforming the Excel data (header promotion, data type changes).
- 🧠 **DAX (Data Analysis Expressions)**: KPI measures, success rate and month-over-month (MoM) growth calculations, plus a custom calendar table.
- 📝 **Data Modeling**: relationships between `All_Transactions`, `All_Users` and `Date_Table` to enable cross-filtering.
- 📁 **File Format**: `.pbit` (Power BI template) for the report and `.png` for the dashboard preview.

---

## 🗂️ Data Source

**Source:** `Phonepe-Final-Dataset.xlsx`, a sample dataset of digital payment transactions and users.

The dataset has two sheets, plus a date table created in DAX:

| Table | Description | Key Columns |
|---|---|---|
| **All_Transactions** | One row per payment transaction | Transaction_ID, Amount, User_ID, Service, Service Type, Payment_Status, Reason, Date |
| **All_Users** | One row per customer | User_ID, Name, Age, Join_Date, Age Segment |
| **Date_Table** (DAX) | Calendar built from transaction dates | Date, Year, Month, Month No., Quarter, Weekday, Day No., Weekend |

---

## ✨ Features / Highlights

### 🔴 Business Problem
Digital payment platforms process millions of transactions every month, but raw transaction logs make it hard to answer key business questions quickly:

- How are transaction volume and value trending month to month?
- How reliable is the payment experience (success vs failure)?
- Which customer age groups drive the most usage?
- Which services (Loans, Insurance, Money Transfer, Recharge & Bills) generate the most value?
- Who are the highest-value customers, and do people transact more on weekdays or weekends?

### 🎯 Goal of the Dashboard
To deliver an interactive visual tool that:
- Tracks overall payment performance through clear KPIs and MoM growth.
- Identifies the services and customer segments that contribute most to revenue.
- Uncovers time-based usage patterns to support marketing, product and operational decisions.

### 🔍 Walkthrough of Key Visuals

1. **Key KPIs (Top Row)**
   - Total Transactions: **300K** (▲ 8.97% MoM)
   - Total Transaction Value: **₹3.47bn** (▲ 8.98% MoM)
   - Unique Users: **108K**
   - Success Rate: **96.00%**

2. **Filter Panel (Month & Payment Status)**: slicers that filter every visual by month or by payment status (e.g. Successful / Failed).

3. **Transactions Over Time (Area/Line Chart)**: compares monthly transaction value and transaction count from Jan to Dec, showing peaks and dips across the year.

4. **Age Segment Contribution (Donut Chart)**: share of users by generation: Gen X (37.4%), Millennials (37.3%), Gen Z (20.74%) and Boomers (4.56%).

5. **Service Transaction Value Analysis (Bar Chart)**: ranks services by transaction value: Loans, Insurance, Money Transfer and Recharge & Bills.

6. **Top 5 Users by Transaction Value (Column Chart)**: highlights the highest-value customers, led by a single user at ₹1.82M.

7. **Weekday vs Weekend Usage (Donut Chart)**: splits transactions into weekday (215K, 71.6%) and weekend (85K, 28.4%).

8. **Insights Card**: a callout summarising the key takeaway: transactions peak on weekdays.

### 💡 Business Impact & Insights

- **Revenue Focus:** **Loans dominate** transaction value (~₹2.5bn, over 70% of the total), far ahead of Insurance (₹0.5bn), Money Transfer (₹0.4bn) and Recharge & Bills (₹0.1bn). Lending is the platform's key revenue driver.
- **Target Audience:** **Gen X and Millennials make up ~75%** of users, so marketing and product features should be built around these groups. Gen Z (~21%) is the main group to grow next.
- **Usage Timing:** **71.6% of transactions happen on weekdays**, which suggests payments are tied to work routines and bill cycles. Weekend offers or cashback campaigns could lift weekend activity.
- **Seasonality:** Transaction value **peaks in July** and dips in **February and September**. This helps with capacity planning and with timing promotional campaigns.
- **Customer Trust:** A **96% success rate** shows a reliable payment system. Analysing the remaining 4% of failures by `Reason` can show where to improve further.
- **Steady Growth:** **~9% month-over-month growth** in both volume and value shows a growing user base and rising engagement.

---

## 🧮 DAX Measures Used

```DAX
Total Transactions        = COUNT(All_Transactions[Transaction_ID])
Total Transactions Value  = SUM(All_Transactions[Amount])
Total Users               = DISTINCTCOUNT(All_Users[User_ID])
Successful Transaction    = CALCULATE([Total Transactions], All_Transactions[Payment_Status] = "Successful")
Success Rate              = DIVIDE([Successful Transaction], [Total Transactions])
Trans Value PM            = CALCULATE([Total Transactions Value], DATEADD(Date_Table[Date], -1, MONTH))
Trans Value MOM%          = DIVIDE([Total Transactions Value] - [Trans Value PM], [Trans Value PM], 0)
Total Trans PM            = CALCULATE([Total Transactions], DATEADD(Date_Table[Date], -1, MONTH))
Total Trans MOM           = DIVIDE([Total Transactions] - [Total Trans PM], [Total Trans PM], 0)
```

---

## ▶️ How to Use

1. Download or clone this repository.
2. Open `PhonePe_Analysis.pbit` in **Power BI Desktop**.
3. When asked, point the data source to `Phonepe-Final-Dataset.xlsx` (**Transform data → Data source settings → Change Source**).
4. Click **Refresh** and explore the dashboard using the filters.

---

## ⚠️ Disclaimer
This is a personal portfolio project built on a sample dataset. It is not affiliated with or endorsed by PhonePe.

## 👤 Author
**Manish Ahire**: [LinkedIn]| linkedin.com/in/manish-ahire-132abb1b5
