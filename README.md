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

## 3. Data Profiling
### 3.1. Data cleaning
Before moving on to the EDA analysis and visualization, the data need to be cleaned and qualified. Then, I implemented following steps:

- Get a brief descriptive statistics
- Fix the datatypes
- Remove duplicates
- Detect outliers
- Check the consistency

**PROBLEM in data cleaning:**
After detecting the outliers by using upper bound/lower bound, I found that in this dataset, there were huge numbers of outliers. These outliers come from 2 factors:
- high price product categories
- numbers of bulk purchases
The ignorance of these outliers may lead to inaccuracy in evaluating the total sales performance. Therefore, instead of eliminating all the values that higher than the upper_bound, I use the following techniques to minimize the effect of outliers:
1. Filter the quantile 0.99 of columns that have outliers.
2. Divide sub-groups: For further analysis, instead of analyze the whole dataset, I divide the product categories into sub-groups depending on their price call "tier". To identify the benchmark of each tier, there are 2 steps:
    - First, mathematically divide the product categories by 3 according to the averge price of each categories to have 3 equal sub-groups.
    - Then, adjust the list in each group by intuitive reasoning.
 
  As the result I identify 3 product tiers:
    - Low-tier: Product categories with avg_price lower than $15
    - Mid-tier: Product categories with avg_price from $15 to $100
    - High-tier: Product categories with avg_price higher than $100

### 3.2. Data Qualifying

```
merged_df = pd.merge(sales_df_cleaned, customer_df, on='CustomerID', how='left')

# Extract the month from the 'Transaction_Date' in the merged_df
merged_df['Month'] = merged_df['Transaction_Date'].dt.strftime('%b') # Extracting abbreviated month name

# Merge the dataframe with discount_df on 'Product_Category' and 'Month'
final_df = pd.merge(merged_df, discount_df, on=['Product_Category', 'Month'], how='left')

final_df.head()
```

## Key Findings
### Sales Trends & Seasonality
- November & December → highest sales (holiday-driven).
- May & June → lowest profitability.
The revenue of the company fluctuated depending on the seasonal factors
- Peak revenue months (Nov, Dec): Driven by holidays and demand for high-value products.
> **Strategy:** Launch targeted holiday campaigns, offer premium bundles, and ensure strong inventory planning.
- Feb, May and June had low revenue. However, each month shows different purchasing patterns of customers: 
  - Feb: This month had a small but highly loyal customer base that made frequent and high-value purchases.
  - May: Sales came from a larger number of customers compared to Feb, but spending per purchase was smaller, and purchase frequency dropped.
  - Jun: Large reach in terms of unique customers, but low engagement — many customers made only once or few purchases.
but the purchase frequency is relatively high: Likely due to repeat purchases of low-priced items bought by a small to high customer number.
> **Strategy:** Use volume discounts, product bundling, and cross-selling to boost average transaction value.
### Product tiers performance
- High-tier products dominate revenue but are heavily skewed toward year-end months.
- Mid-tier products fluctuate, peaking in April; low-tier products remain stable but with low contribution.
### Product Category Insights
- Highest volume categories: Apparel, Nest-USA, Office.
- Lowest volume categories: Gift Cards, Housewares, Android.
- Most profitable categories: Nest-USA, Apparel, Nest.
- Least profitable categories: Waze, Housewares, Android.
- Housewares category: low sales but high quantity sold → potential for premium positioning via limited editions or innovations.

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
