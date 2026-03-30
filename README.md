# PhonePe Data Analysis Dashboard

![PhonePe Dashboard](Icons/ph%20logo.png)

## Overview
This project is an **End-to-End Data Analysis Project using Power BI**, designed to mirror real-world data analysis scenarios. It focuses on analyzing transaction data modeled after a platform like PhonePe. This project covers all the essential data analysis aspects such as transaction tracking, failed payment monitoring, and visualizing multiple services like Insurance, Loans, Money Transfers, and Recharge & Bills.

## Project Structure
The project centers around a highly interactive **5-page Power BI dashboard**, seamlessly linked together using custom navigation buttons.

### 1. Homepage
Provides an overarching summary of all key metrics for a quick overview:
- **Total Transaction Amount:** The total overall amount transacted via PhonePe.
- **Failed Payments:** High-level tracking of failed transactions and the reasons behind them.
- **Date Range Slicer:** Interactive filter allowing users to select different time periods to analyze transactions dynamically.

### 2. Service-Specific Dashboards
Dedicated pages with detailed tracking for four key services:
- 🛡️ **Insurance:** Breaking down transactions into categories like term life, car, and health insurance.
- 💰 **Loans:** Analyzing loan types such as auto and personal loans.
- 💸 **Money Transfers:** Analyzing peer-to-peer and merchant payments.
- 📱 **Recharge & Bills:** Tracking utility bills and mobile recharges.

*Each service page includes vital visualizations:*
- **Amount vs. Month:** A graph showing the total amount transacted each month.
- **Service vs. Amount:** A bar chart displaying the contribution of each sub-service to the total transaction amount.
- **Payment Status:** A pie chart illustrating successful vs. failed payments.

## Failed Payment Analysis
A crucial part of this project is deep-diving into failed payments. By tracking the reasons for failure (e.g., server error, wrong payment details, insufficient balance) using pie charts, businesses can identify operational issues and take corrective actions.

## Dataset Overview
The dashboard is powered by a comprehensive dataset containing detailed transaction records:
- **User Details:** User ID, Name, Age, Join Date.
- **Transaction Information:** Transaction ID, Amount, Service Type, Payment Status, Date.
- **Service Breakdown:** Granular details about each service, including UPI payments, specific insurance premiums, loan types, and recharge categories.

## Dashboard Interactivity & UI
- **Dynamic Filtering:** Extensive use of Power BI slicers ensures the dashboard updates automatically based on user selections (e.g., date ranges).
- **Brand Alignment:** The dashboard is customized with PhonePe’s signature purple color theme to maintain visual consistency, alongside tailored font styles and shadows for a premium UI feel.
- **Seamless Navigation:** Custom buttons in Power BI link the pages (Home, Insurance, Loans, Money Transfer, Recharge & Bills) for intuitive user navigation.

## Tools & Technologies Used
- **Power BI:** For loading data, creating interactive measures, custom buttons, and building the final visual dashboard.

## How to Open and Use
1. **Prerequisites:** Ensure you have [Power BI Desktop](https://powerbi.microsoft.com/desktop/) installed.
2. Clone or download this repository to your local machine.
3. Double-click the `phonepe-dashboard.pbix` file to open it in Power BI Desktop.
4. Use the navigation buttons to explore different service tabs and interact with slicers to dynamically analyze the data.