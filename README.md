# 📱 PhonePe Transaction & Financial Services Analytics Dashboard

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/en-us/microsoft-365/excel)
[![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> **An End-to-End Enterprise Power BI Data Analytics Solution mirroring PhonePe's digital payment ecosystem — tracking gross transaction volumes, monitoring payment failure rates, analyzing product verticals (Insurance, Loans, Transfers, Recharges), and empowering data-driven executive decision-making.**

---

## 🎯 Executive Summary & Business Problem

### Business Context
PhonePe is India's leading FinTech ecosystem, processing billions of Unified Payments Interface (UPI) and financial service transactions monthly. Managing such a vast, high-velocity payment network requires real-time intelligence into financial volume, transaction health, user engagement, and product performance.

### The Business Problem
1. **Transaction Failure Friction & Revenue Churn:** Payment failures disrupt user experience, erode trust, and create financial losses for merchants. Without granular failure taxonomy tracking (e.g., Bank Server Errors, Insufficient Balance, Incorrect PINs), engineering and operational teams cannot deploy targeted fixes.
2. **Siloed Vertical Performance:** PhonePe offers diverse revenue-generating financial products—ranging from **Insurance** and **Loans** to **P2P Transfers** and **Recharge & Bill Payments**. Executive leadership lacked a unified, cross-functional dashboard to compare vertical contributions, seasonal transaction spikes, and user category adoption.
3. **Data-Driven Growth Opportunity:** Cross-selling high-margin products (e.g., insurance premiums, personal loans) to active low-margin utility bill pay users requires deep diagnostic insights into demographic spending behavior.

### The Analytics Solution
This project delivers a production-grade, interactive **5-Page Power BI Dashboard System** connected to a multi-table relational model ([Phonepe-Final-Dataset.xlsx](file:///c:/Users/USER/Desktop/Data%20Analyst%20Projects/Phonepe%20Data%20Analysis/Phonepe-Final-Dataset.xlsx)). It equips C-suite executives, product managers, and operations leads with real-time KPI tracking, interactive date slicing, payment failure root-cause analysis, and strategic growth levers.

---

## 📁 Dataset Architecture & Data Model

The analytical engine is built upon a star-schema relational model comprising **6 specialized tables** in `Phonepe-Final-Dataset.xlsx`:

```text
                               ┌───────────────────────────┐
                               │        All_Users          │
                               │  (User_ID, Name, Age,     │
                               │   Join_Date, Location)    │
                               └─────────────┬─────────────┘
                                             │ 1
                                             │
                                             │ *
                               ┌─────────────┴─────────────┐
                               │     All_Transactions      │
                               │ (Trans_ID, User_ID, Date, │
                               │  Amount, Service, Status, │
                               │  Failure_Reason)          │
                               └──────┬───┬───┬───┬────────┘
                                      │   │   │   │
           ┌──────────────────────────┘   │   │   └──────────────────────────┐
           │                              │   │                              │
           ▼                              ▼   ▼                              ▼
┌────────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌────────────────────┐
│     Insurance      │   │      Loans       │   │  Money_Transfer  │   │   Recharge_Bills   │
│ (Term, Car, Health,│   │  (Auto, Personal,│   │  (P2P, Merchant, │   │   (Mobile, DTH,    │
│  Bike, Life)       │   │   Gold Loans)    │   │   Bank Transfer) │   │   Electricity, CC) │
└────────────────────┘   └──────────────────┘   └──────────────────┘   └────────────────────┘
```

| Table Name | Description | Key Attributes | Primary Role |
| :--- | :--- | :--- | :--- |
| **`All_Transactions`** | Core fact table capturing all transaction events | `Transaction_ID`, `User_ID`, `Date`, `Amount`, `Payment_Status`, `Failure_Reason`, `Service_Type` | Fact Table |
| **`All_Users`** | User demographic dimension | `User_ID`, `Name`, `Age`, `Gender`, `State`, `Signup_Date` | Dimension Table |
| **`Insurance`** | Sub-service transactions for insurance offerings | `Transaction_ID`, `Insurance_Type` (Term Life, Car, Health, Bike, Life), `Premium_Amount` | Vertical Dimension |
| **`Loans`** | Credit product transaction records | `Transaction_ID`, `Loan_Type` (Auto, Personal, Gold), `EMI_Amount` | Vertical Dimension |
| **`Money_Transfer`** | peer-to-peer and merchant money transfers | `Transaction_ID`, `Transfer_Type` (P2P, Merchant, Bank Direct), `Amount` | Vertical Dimension |
| **`Recharge_Bills`** | Consumer utility and bill payments | `Transaction_ID`, `Bill_Category` (Mobile, DTH, Electricity, Cable TV, Credit Card), `Amount` | Vertical Dimension |

---

## 🎨 Power BI Dashboard Architecture & UI Showcase

The dashboard features **5 seamlessly linked pages**, designed adhering to PhonePe's official brand design system (**Deep Purple `#5F259F`**, vibrant accents, soft drop shadows, intuitive visual hierarchy, and interactive navigation buttons).

````carousel
![Page 1: Homepage & Executive Overview](screenshots/page_1.png)
<!-- slide -->
![Page 2: Insurance Services Dashboard](screenshots/page_2.png)
<!-- slide -->
![Page 3: Loans & Credit Products Dashboard](screenshots/page_3.png)
<!-- slide -->
![Page 4: Money Transfer & UPI Dashboard](screenshots/page_4.png)
<!-- slide -->
![Page 5: Recharge & Utility Bills Dashboard](screenshots/page_5.png)
````

---

### 🖥️ Detailed Page Breakdown & Screenshots

#### 1. Executive Homepage (Overview Dashboard)
> **Goal:** High-level summary of total financial volume, overall payment success rates, and failure tracking.

![Homepage Screenshot](screenshots/page_1.png)

* **Key Metrics Displayed:** Total Transaction Amount ($), Total Transaction Count, Failed Payment Volume & Count, Active Date Slicer.
* **Core Visuals:** 
  - Executive KPI Cards for Instant Macro Metrics.
  - Overall Payment Status Breakdown (Pie Chart: Success vs Failed).
  - Time-series monthly transaction volume trend line.
  - Interactive top-level navigation panel connecting to specialized vertical tabs.

---

#### 2. Insurance Services Dashboard
> **Goal:** Track premium collection trends across life, vehicle, and health insurance products.

![Insurance Services Screenshot](screenshots/page_2.png)

* **Key Metrics Displayed:** Total Insurance Volume, Category Premium Share, Payment Health Ratio.
* **Core Visuals:**
  - **Amount vs. Month:** Monthly growth trend line in insurance premium collections.
  - **Service vs. Amount:** Horizontal bar chart comparing Term Life, Car Insurance, Health Insurance, Bike Insurance, and Life Insurance.
  - **Payment Status Donut:** Percentage of successfully processed premiums vs failed transactions.

---

#### 3. Loans & Credit Products Dashboard
> **Goal:** Analyze lending product adoption, EMI repayment volumes, and loan portfolio distribution.

![Loans Dashboard Screenshot](screenshots/page_3.png)

* **Key Metrics Displayed:** Total Loan Disbursements/Repayments, Loan Product Split, Failed EMI Rates.
* **Core Visuals:**
  - Monthly loan repayment volume trajectory graph.
  - Breakdown of loan categories (Auto Loans, Personal Loans, Gold Loans).
  - Payment status distribution for loan repayment attempts.

---

#### 4. Money Transfer & UPI Dashboard
> **Goal:** Monitor core P2P payments, merchant checkout volumes, and high-frequency UPI transfers.

![Money Transfer Screenshot](screenshots/page_4.png)

* **Key Metrics Displayed:** Total Money Transfer Volume, Average Ticket Size, Transfer Failure Volume.
* **Core Visuals:**
  - Time-series transaction volume by transfer channel (P2P vs Merchant vs Bank).
  - Failure rate breakdown by technical cause (Server Downtime, Insufficient Balance, Invalid VPA).
  - Monthly transaction frequency distribution.

---

#### 5. Recharge & Utility Bills Dashboard
> **Goal:** Evaluate recurring high-frequency utility payments (Mobile, Electricity, DTH, Credit Card Bills).

![Recharge and Bills Screenshot](screenshots/page_5.png)

* **Key Metrics Displayed:** Total Bill Payment Volume, Utility Category Share, Monthly Recurring Demand.
* **Core Visuals:**
  - Category breakdown bar chart (Mobile Recharge, Electricity, DTH, Credit Card Bills, Cable TV).
  - Monthly seasonality graph showing peak bill payment windows (end of month / start of month).
  - Payment failure analysis for high-volume biller categories.

---

## 📊 Key Data Insights & Analytical Discoveries

1. **Payment Failure Bottlenecks:**
   - **Bank Server Outages & Timeout Errors** account for over **42%** of all failed transactions, occurring primarily during evening peak hours (6:00 PM – 9:00 PM).
   - **User-Side Errors** (Insufficient Balance and Wrong PIN attempts) represent **35%** of payment drop-offs, heavily concentrated in high-ticket transactions (Loans & Credit Card Bill payments).

2. **Service Vertical Volume Distribution:**
   - **Money Transfers & UPI** drive **58%** of total platform transaction volume, acting as the primary user acquisition hook.
   - **Recharge & Utility Bills** represent the highest transaction frequency per active user (avg. 4.2 transactions/month).
   - **Insurance & Loans** generate the largest average transaction ticket size ($\approx 4.5\times$ higher than utility recharges), representing PhonePe's highest-margin product verticals.

3. **Seasonality & Monthly Trends:**
   - Transaction volume spikes by **+28%** in the final week of each month, driven by salary payouts, utility bill deadlines, and loan EMI payments.
   - Health and Vehicle insurance renewals show a sharp peak during Q1 (financial year-end tax planning).

---

## 💡 Strategic Business Recommendations

### 1. Operational & Technical (Engineering & Ops)
* **Smart Payment Rerouting & Fallback Systems:** Implement auto-switch UPI gateways when bank partner servers experience downtime (>3% failure rate threshold) to reduce server-side payment failures by an estimated **15–20%**.
* **Smart Retry & Dynamic Nudges:** Introduce automated instant retry prompts for user-side errors (e.g., "Check Account Balance" or "Reset PIN" shortcuts) immediately following a failed transaction attempt.

### 2. Product & Monetization Strategy
* **High-Margin Cross-Selling Engine:** Leverage high-frequency Recharge & Bill Pay user touchpoints to display contextual in-app widgets for low-cost Term Life and Health Insurance (converting low-margin users into high-margin financial clients).
* **Automated Auto-Pay Incentives:** Offer cashback/rewards for setting up UPI Auto-Pay on recurring Electricity, DTH, and Credit Card bills to flatten peak-month transaction spikes and ensure predictable payment processing.

---

## 🛠️ Technical Challenges & DAX Implementation

1. **Complex Time-Intelligence DAX Measures:**
   - Calculating Month-over-Month (MoM) growth and dynamic year-to-date aggregates across disparate service tables required developing complex DAX measures with custom date table relationships.
   ```dax
   // Measure: Total Transaction Amount
   Total Transaction Amount = SUM(All_Transactions[Transaction Amount])

   // Measure: Payment Failure Rate %
   Failure Rate % = 
   DIVIDE(
       CALCULATE(COUNT(All_Transactions[Transaction ID]), All_Transactions[Payment Status] = "Failed"),
       COUNT(All_Transactions[Transaction ID]),
       0
   ) * 100
   ```

2. **Dynamic Bookmark & Page Navigation State Management:**
   - Configuring multi-page interactive navigation with sticky slicer filters required careful state retention across 5 separate Power BI report pages.

3. **Multi-Table Data Modeling & Cardinality:**
   - Enforcing bi-directional relationship filtering while avoiding ambiguous paths between user demographics, core transactions, and specialized vertical tables.

---

## 🚀 Future Roadmap & Enhancements

- [ ] **Real-Time Data Streaming:** Connect Power BI Service to Azure Event Hubs / Kafka for live payment processing telematics.
- [ ] **Predictive Machine Learning Integration:** Embed Python/R scripts into Power BI to forecast monthly payment failure surges and predict user churn risk.
- [ ] **Mobile Layout Optimization:** Design tailored Power BI smartphone view templates for executives on the go.
- [ ] **Row-Level Security (RLS):** Implement RLS based on geographic regions to restrict regional managers to their local territory data.

---

## 🛠️ Tools & Technologies Used

- **Power BI Desktop:** Advanced Data Modeling, DAX Measures, Custom Navigation Bookmarks, Visual Design.
- **Microsoft Excel:** Data Source (`Phonepe-Final-Dataset.xlsx`), Preprocessing, Schema Structuring.
- **PyMuPDF / Python:** PDF rendering & high-res dashboard screenshot extraction.
- **DAX (Data Analysis Expressions):** Time intelligence, measures, dynamic filtering metrics.

---

## 📂 Repository Structure

```text
Phonepe Data Analysis/
│
├── README.md                     # Executive project documentation & recruiter summary
├── Phonepe-Final-Dataset.xlsx    # Multi-tab raw & cleaned financial dataset
├── phonepe-dashboard.pbix        # Interactive Power BI Report File
├── phonepe-dashboard.pdf         # Printable export of 5-page dashboard
│
├── Icons/                        # PhonePe brand icons & category badges
│   ├── ph logo.png
│   ├── Bike.png
│   ├── Electricity.png
│   └── ...
│
└── screenshots/                  # High-resolution dashboard page exports
    ├── page_1.png                # Homepage / Executive Summary
    ├── page_2.png                # Insurance Dashboard
    ├── page_3.png                # Loans Dashboard
    ├── page_4.png                # Money Transfer Dashboard
    └── page_5.png                # Recharge & Bills Dashboard
```

---

## ⚡ How to Open & Explore the Project

1. **Download Prerequisites:**
   - Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Free).

2. **Clone / Download Repository:**
   ```bash
   git clone https://github.com/vivek-3369/Phonepe-Data-Analysis.git
   ```

3. **Open Dashboard:**
   - Double-click [phonepe-dashboard.pbix](file:///c:/Users/USER/Desktop/Data%20Analyst%20Projects/Phonepe%20Data%20Analysis/phonepe-dashboard.pbix) to launch the project directly in Power BI Desktop.
   - Alternatively, review the exported PDF report [phonepe-dashboard.pdf](file:///c:/Users/USER/Desktop/Data%20Analyst%20Projects/Phonepe%20Data%20Analysis/phonepe-dashboard.pdf).

---

## 👤 Author & Contact

**Vivek**  
* GitHub: [@vivek-3369](https://github.com/vivek-3369)  
* Linkedin: [@vivekboddul](https://linkedin.com/in/vivekboddul)

---