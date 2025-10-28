# Customer_Behavior_Analysis-with-Dashboard
Data Analysis of Customer behavior using Python, MySQL and PowerBI
# 📊 Customer Behavior Analysis Dashboard

> **End-to-end data analysis project** analyzing customer purchasing patterns, subscription trends, and revenue insights using Python, MySQL, and Power BI.

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Dataset](#dataset)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Analysis & Insights](#analysis--insights)
- [Dashboard](#dashboard)
- [Key Learnings](#key-learnings)
- [Future Enhancements](#future-enhancements)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Project Overview

This project performs comprehensive analysis of customer behavior data to uncover actionable insights for business decision-making. The analysis focuses on:

- **Customer Segmentation**: Identifying purchasing patterns across demographics
- **Revenue Analysis**: Understanding revenue drivers by category and age group
- **Subscription Trends**: Analyzing factors influencing subscription status
- **Product Performance**: Ranking top-performing items per category

**Business Problem**: How can businesses optimize product offerings and marketing strategies based on customer purchasing behavior?

---

## ✨ Features

- 🔍 **Data Cleaning & Preprocessing** with Python (pandas)
- 💾 **Database Management** using MySQL
- 📊 **Interactive Dashboard** built in Power BI
- 📈 **Statistical Analysis** including window functions and aggregations
- 🎨 **Professional Visualizations** with custom color palettes
- 🔄 **Automated Data Pipeline** from MySQL to Power BI

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **Python 3.x** | Data cleaning, preprocessing, and analysis |
| **Pandas** | Data manipulation and transformation |
| **MySQL 8.0** | Database creation and complex queries |
| **Power BI Desktop** | Interactive dashboard and visualizations |
| **Jupyter Notebook** | Analysis documentation |

---

## 📁 Dataset

**Size**: 3,900 customer records

**Features**:
- `customer_id`: Unique identifier
- `age`: Customer age
- `gender`: Customer gender (Male/Female)
- `item_purchased`: Product name
- `category`: Product category (Clothing, Accessories, Footwear, Outerwear)
- `purchase_amount`: Transaction value ($)
- `location`: Customer location
- `size`: Product size
- `color`: Product color
- `season`: Purchase season
- `review_rating`: Customer rating (1-5)
- `subscription_status`: Yes/No
- `payment_method`: Payment type
- `shipping_type`: Delivery method
- `discount_applied`: Yes/No
- `promo_code_used`: Yes/No
- `previous_purchases`: Number of past purchases
- `frequency_of_purchases`: Purchase frequency category

---

## 🚀 Installation

### Prerequisites
- Python 3.8+
- MySQL 8.0+
- Power BI Desktop
- Jupyter Notebook

### Setup Instructions

1. **Clone the repository**
2. **Install Python dependencies**
3. **Set up MySQL database**
CREATE DATABASE customer_behavior;
USE customer_behavior;
-- Run the SQL schema file
SOURCE scripts/create_tables.sql;
4. **Load data into MySQL**
python scripts/load_data.py

5. **Open Power BI Dashboard**
- Open `Customer_Behavior_Dashboard.pbix` in Power BI Desktop
- Update data source connection to your local MySQL instance
- Refresh data

---

## 📂 Project Structure
Customer_Behavior_Analysis-with-Dashboard/
├── data/
│ ├── raw/ # Original dataset
│ └── processed/ # Cleaned data
├── notebooks/
│ ├── 01_data_cleaning.ipynb # Data preprocessing
│ └── 02_analysis.ipynb # Exploratory analysis
├── sql/
│ ├── create_tables.sql # Database schema
│ └── queries.sql # Analysis queries
├── dashboard/
│ └── Customer_Behavior_Dashboard.pbix
├── scripts/
│ └── load_data.py # Data loading script
├── images/
│ └── dashboard_preview.png # Screenshots
├── requirements.txt
├── LICENSE
└── README.md



---

## 🔍 Analysis & Insights

### Key SQL Queries Implemented

**1. Top 3 Items per Category**

WITH item_counts AS (
SELECT category, item_purchased,
COUNT(customer_id) AS total_orders,
ROW_NUMBER() OVER (PARTITION BY category
ORDER BY COUNT(customer_id) DESC) AS item_rank
FROM customer
GROUP BY category, item_purchased
)
SELECT category, item_purchased, total_orders
FROM item_counts
WHERE item_rank <= 3;


**2. Subscription Analysis for Repeat Buyers**
SELECT subscription_status,
COUNT(customer_id) AS repeat_buyers
FROM customer
WHERE previous_purchases > 5
GROUP BY subscription_status;


**3. Revenue by Age Group**
SELECT age_group,
SUM(purchase_amount) AS total_revenue
FROM customer
GROUP BY age_group
ORDER BY total_revenue DESC;
SELECT age_group,
SUM(purchase_amount) AS total_revenue
FROM customer
GROUP BY age_group
ORDER BY total_revenue DESC;


### Business Insights

✅ **Customer Demographics**: Young Adults generate the highest revenue

✅ **Product Performance**: Clothing category leads in both sales and revenue

✅ **Subscription Behavior**: 27% of customers are subscribed (73% opportunity for growth)

✅ **Purchase Patterns**: Repeat buyers (>5 purchases) show higher subscription rates

---

## 📊 Dashboard

The Power BI dashboard includes:

### KPI Cards
- 📌 Total Customers: **3.9K**
- 💰 Average Purchase Amount: **$59.76**
- ⭐ Average Review Rating: **3.75/5**

### Visualizations
- 🥧 **Subscription Status** (Donut Chart)
- 📊 **Revenue by Category** (Bar Chart)
- 📈 **Sales by Category** (Column Chart)
- 📉 **Revenue by Age Group** (Horizontal Bar)
- 🎯 **Sales by Age Group** (Horizontal Bar)

### Interactive Features
- Gender filter (Male/Female)
- Category filter (Clothing, Accessories, Footwear, Outerwear)
- Shipping Type filter
- Drill-through capabilities
- Cross-report filtering

---

## 💡 Key Learnings

### Technical Skills Developed
- Advanced SQL window functions (`ROW_NUMBER()`, `PARTITION BY`)
- Python data cleaning with pandas
- Power BI DAX formulas and data modeling
- MySQL database design and optimization
- Creating automated ETL pipelines

### Challenges Overcome
- ✅ Connecting MySQL to Power BI (authentication issues)
- ✅ Handling missing/inconsistent data
- ✅ Optimizing complex SQL queries for performance
- ✅ Designing intuitive dashboard layouts

---

## 🚀 Future Enhancements

- [ ] Add predictive modeling for customer churn
- [ ] Implement RFM (Recency, Frequency, Monetary) analysis
- [ ] Create Python Flask web app for dashboard
- [ ] Add real-time data refresh capabilities
- [ ] Expand analysis to include seasonal trends
- [ ] Deploy dashboard to Power BI Service

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Contact

**Mohammed Shakeeb**

- GitHub: [@Shaksninja](https://github.com/Shaksninja)
- LinkedIn: www.linkedin.com/in/mohammed-shakeeb-b7357899
- Email: shakeeb10@gmail.com

---

## 🙏 Acknowledgments

- Inspired by real-world e-commerce analytics challenges
- Special thanks to the data analysis community

---

⭐ **If you found this project helpful, please consider giving it a star!**

---

**Project Status**: ✅ Complete | 📅 Last Updated: October 2025


