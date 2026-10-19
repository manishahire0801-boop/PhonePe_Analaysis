📊 PhonePe Payment Insights Dashboard (Power BI)

An interactive Power BI dashboard that analyses digital payment transactions to show
how users pay, what they pay for, and when they pay the most.

![Dashboard Preview](dashboard.png)

🎯 Objective
Turn raw transaction and user data into clear business insights: transaction growth,
payment success, customer segments and service-level revenue.

📈 Key Metrics (KPIs)
| KPI | Value |
| Total Transactions | 300K (▲ 8.97% MoM) |
| Total Transaction Value | ₹3.47bn (▲ 8.98% MoM) |
| Unique Users | 108K |
| Success Rate | 96.00% |

🖼️ Dashboard Features
- Transactions Over Time: monthly trend of transaction count and value
- Age Segment Contribution: Gen X, Millennials, Gen Z and Boomers
- Service Transaction Value Analysis: Loans, Insurance, Money Transfer, Recharge & Bills
- Top 5 Users by transaction value
- Weekday vs Weekend Usage
- Interactive filters for Month and Payment Status

💡 Key Insights
- Loans are the largest category by value (~₹2.5bn), far ahead of Insurance (₹0.5bn) and Money Transfer (₹0.4bn).
- Gen X (37.4%) and Millennials (37.3%) together make up ~75% of the user base.
- 71.6% of transactions happen on weekdays.
- Transaction value peaks in July and dips in February and September.
- A 96% success rate shows a reliable payment experience.

🛠️ Tools & Techniques
- Power BI Desktop
- Power Query: data loading, header promotion, type transformation
- Data Modelling: relationships between Transactions, Users and a Date table
- DAX: custom calendar table and measures, including time intelligence

DAX Measures Used

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

🗂️ Data Model
| Table | Columns |
| All_Transactions | Transaction_ID, Amount, User_ID, Service, Service Type, Payment_Status, Reason, Date |
| All_Users | User_ID, Name, Age, Join_Date, Age Segment |
| Date_Table (DAX) | Date, Year, Month, Month No., Quarter, Weekday, Day No., Weekend |

📁 Repository Structure
├── PhonePe_Analysis.pbit  Power BI template
├── Phonepe-Final-Dataset.xlsx  Dataset
├── dashboard.png  Dashboard screenshot
└── README.md


▶️ How to Use
1. Download or clone this repository.
2. Open `PhonePe_Analysis.pbit` in Power BI Desktop.
3. When asked, point the data source to `Phonepe-Final-Dataset.xlsx`
   (Transform data → Data source settings → Change Source).
4. Click **Refresh** and explore.

⚠️ Disclaimer
This is a personal portfolio project built on a sample dataset. It is not affiliated
with or endorsed by PhonePe.

👤 Author
Manish Ahire: feel free to connect on [LinkedIn]|  linkedin.com/in/manish-ahire-132abb1b5
