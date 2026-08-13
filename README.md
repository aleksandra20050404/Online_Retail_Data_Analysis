# Online Retail Customer Churn Analysis

## Table of Content
- [Project Background](#project-background)
- [Overview of Findings ](#overview-of-findings) 
- [Data Analysis](#data-analysis) 
- [Recommendations](#recommendations)
- [Summary](#summary)

# Project Background
This report analyzes the provided "Online Retail" dataset to gain insights into sales performance, customer behavior, and potential churn. The analysis includes data loading, cleaning, exploration, feature engineering, and visualization, culminating in an RFM (Recency, Frequency, Monetary) analysis and a churn analysis.

### Objectives 
Exploratory data analysis is performed to achive following business goals : 
Engineer relevant features for future customer analysis.
Visualize key findings in  sales trends, product popularity, and geographical distribution of sales.
Conduct an RFM analysis to segment customers based on their purchasing behavior.
Perform a churn analysis to identify customers who are at risk of leaving.a
#Project Overview

### Tools Used
- Numpy
- Pandas
- Matplotlib
- Seaborn
- Plotly

### Files
- **Online_Retail_Data_Analysis**: The main Jupyter Notebook file with data analysis.
- **README.md**: This file provides an overview of the repository and instructions for using and accessing the Jupyter Notebook.
- **requirments.txt**: Copy and paste the content from this file to  install all the specified libraries and their versions.

### Data Source
Data obtained from the UCI Machine Learning Repository (extract in Excel format) 
 can be found [here](https://archive.ics.uci.edu/static/public/352/online+retail.zip)

### Author
[Aleksandra Vislova](https://www.linkedin.com/in/aleksandra-vislova-a51ba9297?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app
)

# Overview of Findings 
### Executive summary 

**Key Conclusions from Sales trends :**

The United Kingdom is the overwhelmingly dominant market, accounting for the vast majority of sales. This suggests a heavy reliance on the UK for revenue, which could pose a risk if market conditions in the UK change.

Market diversification: The United Kingdom is the dominant market, with significantly higher sales compared to other countries. Reduce reliance on the UK market by looking at expansion into other countries, especially as an online retailer can operate globally.

![image](https://github.com/user-attachments/assets/12f1951a-0f04-4b52-a1bf-bc24c76bfa9f)

Seasonal Marketing Campaign: Use the "hockey curve" sales trend to plan targeted marketing and promotions for the end of the year. 

![image](https://github.com/aleksandra20050404/OnlineRetail_Data_Analysis/blob/main/img/monthly_sales.png)


Potential Inventory issues: The low percentages (all under 2%) could imply either a lack of standout products that drive significant sales or an overly broad product catalog diluting focus. Alternatively, it might reflect a business model that relies on high-volume, low-margin sales across many products. 

![image](https://github.com/aleksandra20050404/OnlineRetail_Data_Analysis/blob/main/img/product_wise_sales.png)

Investment in marketing campaigns to pair top products with complementary items (e.g., bundle Regency Cake Stand 3 Tier with Party Bunting for event hosting) will increase average order value. 

### RFM analysis

RFM Analysis demonstrated  healthy customer value distribution nearly evenly split (Low: 35%, Medium: 29%, High: 29%), indicating diversified revenue streams rather than over-reliance on one segment.

Based on Churn Analysis addressing 0–30 day churn could recover 60–70% of at-risk revenue based on density concentration. nvestigate early churn drivers (e.g., quality issues, delivery delays) through customer interviews. Set targets to increase average customer lifespan by tracking "Days to Churn"
![image](https://github.com/aleksandra20050404/OnlineRetail_Data_Analysis/blob/main/img/distribution_for_churnged_customers.png)


For Mid-Term retention customers implement personalized reactivation strategies to segment users by past behavior, such as category preference and send personalized product recommendations monthly.

# Data Analysis

[View full Jupyter Notebook](https://github.com/aleksandra20050404/OnlineRetail_Data_Analysis/blob/main/Online_Retail_Data_Analysis.ipynb)

### Step 1: Loading Data and installing modules
Original dataset was downloaded from 
The dataset was loaded from a zipped file containing an Excel file.

### Step 2: Data Preparation:

### Data Cleansing Assumptions : 

- Some negative Quantity and UnitPrice values ​​have been removed based on error assumptions, which must be confirmed by the database owners.
- Initial data exploration revealed missing values in 'CustomerID' and 'Description', and negative values in 'Quantity' and 'UnitPrice'.
- Missing 'Description' values were imputed by using the most frequent description for each 'StockCode'.
Rows with missing 'CustomerID' were dropped, as this column is crucial for customer-level analysis.

### Step 3: Feature Engeneering: 
For further analysis, new columns were created:
A 'TotalPrice' column was created by multiplying 'Quantity' and 'UnitPrice'.
A 'Month' column was extracted from the 'InvoiceDate' for time-based analysis.

### Step 4: Data Analysis
#### Data Visualization of Monthly Sales, Product-wise Sales, Country-wise Sales:

### **Monthly Sales:** 
A line plot of monthly sales showed clear seasonality. Sales were lower at the beginning of the year, stabilized in the middle, and peaked significantly in the last quarter, particularly in November. This suggests a strong holiday shopping effect.

### **Product-wise Sales:**
A horizontal bar chart of the top 5 products by sales revealed a low concentration of sales in the top products. The highest-selling product accounted for less than 2% of total sales, indicating a broad product catalog with sales spread across many items.

### **Country-wise Sales:** 
A bar chart of the top 5 countries by sales highlighted the overwhelming dominance of the United Kingdom as the primary market. Other countries had significantly lower sales contributions.

### RFM Analysis
RFM metrics (Recency, Frequency, Monetary) were calculated for each customer.
- Recency - defined as the number of days since the customer's last purchase.
- Frequency - the number of unique invoices per customer.
- Monetary - the sum of total price per customer.

RFM scores (1-4 scale) were assigned based on quantiles of the RFM metrics, using ranking to handle ties. Lower recency, higher frequency, and higher monetary values received higher scores.
An RFM sum was calculated as the sum of the individual RFM scores. Customers with higher RFM sums represent the most valuable customers.

### **Churn Analysis**
Churned customers were identified as those who had not made a purchase in the last 90 days.
The distribution of days since last purchase for churned customers was visualized using a histogram and KDE plot.
The total number of churned customers was calculated.

# Recommendations
Based on the analysis conducted, the following recommendations can be proposed:

**Sales Trend :** Develop targeted marketing campaigns to capitalize on the peak sales season in the last quarter.
**Product Trend:** investigate strategies to increase sales in underperforming markets.

**RFM and Customer Churn Analysis :**

- Healthy Value Distribution: Customer value tiers are nearly evenly split (Low: 35%, Medium: 29%, High: 29%), indicating diversified revenue streams rather than dangerous over-reliance on one segment.
- The substantial Low Value segment (1,504 customers) presents untapped potential for revenue growth through tier migration.
- Focus on migrating Low Value customers to Medium Value status.
- High Churn Concentration at Low Recency (0-30 Days)

The density plot shows a sharp peak near 0-30 days since the last purchase. This indicates that customers who churn typically do so very soon after their most recent purchase, suggesting dissatisfaction with their purchase, poor onboarding, or lack of post-purchase engagement. Providing time-limited discounts (next purchase within 14 days) to encourage rapid repeat buys or launching  automated post-purchase surveys to address dissatisfaction. 

Mid-Term Retention (30-150 Days)
Personalized Reactivation:
Segment users by past behavior (e.g., category preference) and send personalized product recommendations monthly.

Long-Tail Churn (Beyond 200 Days)
Secondary Risk Group: A smaller but significant group of customers churns after 200+ days of inactivity. These are likely "dormant" customers who gradually disengage due to perceived irrelevance or competitive offerings.
Deploy churn surveys to uncover systemic issues
Revenue Leakage: While less dense, this group represents accumulated lost revenue over time.

# Summary
The business has a diversified product portfolio with no single product dominating sales, which reduces risk but also highlights a lack of standout performers. Stakeholders should focus on promoting top products like Dotcom Postage and Regency Cake Stand 3 Tier, while reassessing the value of underperforming items like Party Bunting. Streamlining the product catalog, optimizing pricing, and leveraging cross-selling opportunities can help drive overall sales growth and improve profitability.



