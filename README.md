# **Investigating business performance and determining factors to increase sales 💸**
## 1. Project Overview:
### Introduction:

### Purposes:
1. Analyze sales performance across product categories to uncover improvement opportunities.
2. Determine factors that influence sales. 
### Outcomes:
1. Identify months that have highest sales volume.
2. 
3. Understand high potential product categories and low potential product categories.
4. Give actionable recommendations for sales improvements.

## 2. Dataset Overview
### 2.1. Data Sources
The dataset in this project is collected from dataset publicly posted on Kaggle 
- Link of dataset: https://www.kaggle.com/code/arpitppatel/marketing-insights-for-e-commerce-company
- Number of records: 52924 rows
### 2.2. Data structure
The dataset includes 4 tables with the following information:
**Table Name: CustomerData.xlsx** – Contains the core demographic details of customers.
- **CustomerID:** A unique identifier assigned to each customer (Type: Numeric) 
- **Gender:** Indicates the customer’s gender. (Type: Categorical (Male, Female))
- **Location:** Specifies the customer’s place of residence. (Type: Categorical (City/Region))
- **Tenure_Months:** Represents the number of months the customer has been associated with the platform. (Type: Numeric)

**Table Name: Discount_Coupon.csv** – Provides details of discount coupons across product categories and months.
- **Month:** Indicates the month in which the coupon was available. (Type: Categorical (Month names/values))
- **Product_Category:** Refers to the category of products eligible for the coupon. (Type: Categorical)
- **Coupon_Code:** The specific code assigned to a discount coupon for a product category in a given month. (Type: Alphanumeric)
- **Discount_pct:** Specifies the discount percentage offered by the coupon. (Type: Numeric (percentage))

**Table Name: Online_Sales.csv** – Contains transactional data at the sales order level.
- **CustomerID:** Unique identifier linking each transaction to a customer. (Type: Numeric) 
- **Transaction_ID:** A unique ID representing each sales transaction. (Type: Alphanumeric)
- **Transaction_Date:** The date on which the transaction occurred. (Type: Date) 
- **Product_SKU:** Unique identifier for the purchased product. (Type: Alphanumeric)
- **Product_Description:** A descriptive label or name of the product. (Type: Text)
- **Product_Category:** Classification of the purchased product. (Type: Categorical)
- **Quantity:** The number of product units purchased in the transaction. (Type: Numeric)
- **Avg_Price:** The price per unit of the product. (Type: Numeric)
- **Delivery_Charges:** Additional delivery fees applied to the order. (Type: Numeric)
- **Coupon_Status:** Denotes whether a discount coupon was applied during the transaction. (Type: Categorical (Used, Not Used, Clicked))


## Key Findings
### Sales Trends & Seasonality
- November & December → highest sales (holiday-driven).
- May & June → lowest profitability.
- High-tier products dominate revenue but are heavily skewed toward year-end months.
- Mid-tier products fluctuate, peaking in April; low-tier products remain stable but with low contribution.
### Product Category Insights
- Highest volume categories: Apparel, Nest-USA, Office.
- Lowest volume categories: Gift Cards, Housewares, Android.
- Most profitable categories: Nest-USA, Apparel, Nest.
- Least profitable categories: Waze, Housewares, Android.
- Housewares category: low sales but high quantity sold → potential for premium positioning via limited editions or innovations.
## Marketing Spend Impact
- Certain months show a strong positive correlation between marketing spend and sales (particularly in peak seasons).
- Off-season marketing spend is less effective unless targeted toward promotions or new product launches.
# Recommendations
## Product Strategy
- Focus on premium product programs for high-value items.
- Apply discounts and bulk deals for mid-tier products to drive quantity sales.
- Reposition low-tier products with creative bundles or niche targeting.
## Marketing Investment
- Increase marketing spend in months with historically high responsiveness (Nov–Dec).
- Implement targeted campaigns in low-sales months to reduce seasonality gaps.
## Category Optimization
- Prioritize high-profit categories like Nest-USA and Apparel in advertising.
- Phase out or rebrand underperforming categories (e.g., Waze, Android) unless strategic for brand image.
# Limitations
- Lack of information related to the market growth rate of each product categories. Otherwise, I can suggest comprehensive strategies to  
