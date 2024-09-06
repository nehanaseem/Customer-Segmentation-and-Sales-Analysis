# 📊Customer Segmentation and Sales Analysis

## 🌟 Project Overview:
This project focuses on analyzing a retail company's sales data to better understand customer behavior and identify key sales trends. The goal is to segment customers based on their purchasing patterns, analyze sales trends, and provide actionable insights to enhance the company's sales strategy.

## 🗂️ Dataset:
The dataset includes the following columns:
Customer ID: Unique identifier for each customer.
Order ID: Unique identifier for each order.
Order Date: Date when the order was placed.
Product ID: Unique identifier for each product.
Product Name: Name of the product.
Category: Category of the product.
Quantity: Number of units sold.
Unit Price: Price per unit of the product.
Total Amount: Total amount for the order (Quantity x Unit Price).
Region: The region from where the order was placed.

## 🛠️ Tasks Completed
### 1. Data Cleaning
Handled Missing Values: Filled missing values with 0.
Standardized Date Format: Ensured consistent date formatting.
Removed Duplicates: Cleaned up any duplicate records.

### 2. Customer Segmentation
RFM Analysis: Performed Recency, Frequency, and Monetary analysis to segment customers.
Customer Segments: Identified key segments such as High-Value Customers, At-Risk Customers, and New Customers.

### 3. Sales Trend Analysis
Monthly Sales Trends: Analyzed sales trends on a monthly basis.
Yearly Sales Trends: Examined sales trends on a yearly basis.
Product Categories: Determined the performance of various product categories.
Regional Sales: Identified regions with the highest and lowest sales.

### 4. Data Visualization
Monthly Sales Trends: Line chart showcasing sales trends over months.
Yearly Sales Trends: Line chart depicting sales trends over years.
Product Category Performance: Bar chart illustrating sales by product category.
Sales by Region: Pie chart showing the distribution of sales across regions.

### 5. Recommendation Report
Findings and Insights: Summarized key findings from the analysis.
Actionable Recommendations: Suggested strategies for targeting different customer segments to boost sales..

## 🛠️ Tools and Libraries Used:
Python: For data manipulation and analysis.
Pandas: For data cleaning and manipulation.
Matplotlib: For creating visualizations.
Seaborn: For enhanced and aesthetically pleasing visualizations.
Jupyter Notebook / Google Colab: For coding and analysis.

## 💻 Code Examples

### Data Cleaning
import pandas as pd

####  Load the dataset
df = pd.read_csv('sales_data.csv')

####  Fill missing values with 0
df.fillna(0, inplace=True)

####  Convert 'Order Date' to datetime format
df['Order Date'] = pd.to_datetime(df['Order Date'], format='%Y-%m-%d')


####  Convert 'Order Date' to datetime format
df['Order Date'] = pd.to_datetime(df['Order Date'], format='%Y-%m-%d')

### Customer Segmentation

####  Calculate Recency
df['Recency'] = (df['Order Date'].max() - df['Order Date']).dt.days

#### Group by 'Customer ID' and calculate Recency, Frequency, and Monetary
recency_df = df.groupby('Customer ID')['Recency'].mean().reset_index()
frequency_df = df.groupby('Customer ID')['Order ID'].count().reset_index()
monetary_df = df.groupby('Customer ID')['Total Amount'].sum().reset_index()

####  Merge and calculate RFM scores
rfm_df = recency_df.merge(frequency_df, on='Customer ID').merge(monetary_df, on='Customer ID')

### Data Visualization

import matplotlib.pyplot as plt
import seaborn as sns

####  Line chart for Monthly Sales Trends
plt.figure(figsize=(12, 6))
sns.lineplot(data=monthly_sales, x='Month', y='Total Amount', hue='Year', marker='o')
plt.title('Monthly Sales Trends')
plt.xlabel('Month')
plt.ylabel('Total Amount')
plt.legend(title='Year')
plt.grid(True)
plt.show()

## 🔍 Insights and Recommendations
High-Value Customers: Target this segment with exclusive offers and loyalty programs to retain them.
At-Risk Customers: Re-engage with personalized marketing strategies to reduce churn.
New Customers: Convert these customers into repeat buyers with special promotions and follow-ups.

## 🚀 Future Work
Analyze the impact of marketing campaigns on customer behavior.
Explore additional segmentation techniques for deeper insights.
Implement predictive modeling to forecast future sales trends.
