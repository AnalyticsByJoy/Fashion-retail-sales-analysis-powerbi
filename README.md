# Fashion Retail Sales Insights | Data Modeling, DAX & Performance Insights (2020–2024)

## Table Of Contents

[👥 Customer Insights | page 2](#customer-insights-|-page-2)




## Project Overview
This project analyzes five years (2020–2024) of retail fashion data to evaluate financial performance, customer behavior, product dynamics, and store efficiency using Power BI.
The goal was not just to visualize sales metrics, but to build a clean, scalable data model capable of supporting reliable multi-dimensional analysis.
The dashboard delivers interactive insights across:
- Revenue, profit, margin, and order trends over time
- Customer segmentation (age, gender, city, loyalty status)
- Product performance by category, supplier, size, color, and season
- Regional and store-level contribution analysis
- Online vs physical store comparison
- Store size efficiency analysis
Beyond surface-level reporting, the project focuses on identifying stability patterns, diversification strength, and structural growth opportunities within the business.
The result is a four-page interactive dashboard built on a structured relational model with optimized DAX measures and time-intelligence capabilities.

## Process
### Data Source:
The dataset used for this analysis contains:
#### Sales Data 
1. Transaction Id
2. Date
3. Product id 
4. Store id
5. Customer id
6. Quantity 
7. Discount
8. Returned 
#### Customer data 
1. Customer id
2. Age
3. Gender
4. City
5. Email
#### Product data
1. Product id
2. Category 
3. Color
4. Size
5. Season
6. Supplier
7. Cost price
8. Must price 
#### Store data
1. Store id
2. Store name
3. Region
4. Store size

### Data Loading (Power query):
- Loaded the four raw tables: sales, customers, products, stores.
- Checked column names, data types, and sample values → noticed messy IDs, potential nulls, inconsistent text.

### Data Cleaning and Transformation 
- Trimmed whitespace from all ID and text columns (Customer ID, Product ID, Store ID, City, Category, etc.).
- Standardized case (lowercase/uppercase) on text fields where needed.
- Replaced blank/null values in Sales[Customer ID] with "Guest" (so guest sales could be tracked properly instead of disappearing in joins).
- Removed duplicates in dimension tables (Customer, Product, Store) on their ID columns to satisfy relationship uniqueness rules.
- Changed data types: IDs → Whole Number or Text (consistent), dates → Date, prices/quantities → Decimal Number or Currency.
- Created Age Group column in Customer table using Conditional Column (or Custom Column with if-then logic): Under 18, 18-24, 25-34, 35-44, 45-54, 55-64, 65+.
- Closed & Applied → data was now clean enough for relationships.

### Data modelling 
- Defined Sales as the fact table (center) and Customer, Product, Store, and Date as dimension tables.
- Built one-to-many relationships (Single direction from dimension to Sales): Customer[Customer ID] → Sales[Customer ID]
Product[Product ID] → Sales[Product ID]
Store[Store ID] → Sales[Store ID]
- Created DAX measures to calculate:
1. Total Revenue
2. Total Profit
3. Profit Margin
4. Average Order Value
5. Total store
6. Repeat customer rate %
7. Revenue from guests%
8. Total unique customers 
9. Average spend per customer
10. Total product
11. Returned orders
12. Total cost
13. Average revenue per store

### Visualization
- Designed a clean, professional, and interactive 4-page Power BI dashboard tailored to the retail fashion sales dataset.
- Interactive slicers on each page for dynamic filtering.
- sorting (descending), and Top N filters where needed.
- Logical flow: high-level KPIs → trends → breakdowns → detailed tables.
- Used line charts, bar charts, pie charts, column charts, donut charts, and tables to present insights clearly.

### Formatting and branding 
- Consistent dark green/gray theme with light backgrounds for readability.
- Clear titles, data labels.
- Mobile-friendly layout
-considerations applied.

### Tools used 
- Power query
- Microsoft Power BI

### Project Insights 

#### 📊 Sales Overview | page 1
![image](https://github.com/user-attachments/assets/29f58199-979a-4fea-8efa-ab299cc31a89)

Over the five-year period (2020–2024), the fashion retail business generated strong and consistent financial performance with stable profitability and minimal volatility.

##### Questions Answered:
- How has revenue, profit, and profit margin evolved from 2020–2024?
- What is the average order value?
- Which year delivered peak financial performance, and how stable are margins over time?
- Which months of each year delivered peak financial perfomance?

###### Key performance indicators:
- Total Revenue: $13M
- Total Profit: $7.8M
- Average Profit Margin: ~59.57%
- Average order value : 262.63

###### Yearly trends on revenue & profit:
2020
- Revenue: ~$2.64M
- Profit: ~$1.559M
- Profit Margin: ~59.14%
- A strong baseline year with healthy  margins.
  
2021
- Revenue: $2.59M (lowest year)
- Profit: ~$1.536M
- Profit Margin: ~59.41%
- Slight revenue dip but profitability remained stable.

2022
- Revenue: ~$2.60M
- Profit: ~$1.546M
- Profit Margin: ~59.38%
- Performance stabilized after the small decline in 2021.

2023
- Revenue: $2.68M (highest year)
- Profit: $1.607M
- Profit Margin: ~59.96%
- Peak performance year with the highest sales and profitability.

2024
- Revenue: ~$2.63M
- Profit: ~$1.577M
- Profit Margin: ~59.94%
- Slight normalization after the 2023 peak.

###### Monthly trends on revenue and profit:

2020 – July was the standout month, achieving $241,793 in revenue and $141,458 in profit, closely followed by October. February recorded the lowest performance ($201,598 revenue, $119,587 profit), showing early-year softness.

2021 – May led in revenue ($234,871) while October captured the highest profit ($140,624). December was the weakest month for both revenue and profit, indicating year-end slowdown.

2022 – May again dominated in both revenue ($237,848) and profit ($144,075), with March close behind. November was the lowest month ($194,545 revenue, $115,860 profit), suggesting end-of-year softness persisted.

2023 – May continued as the strongest month ($241,585 revenue, $145,833 profit), followed by November. February was again the slowest ($198,308 revenue, $115,350 profit), consistent with prior years.

2024 – May led once more ($238,093 revenue, $146,054 profit), with April slightly behind. November showed the lowest monthly figures ($207,859 revenue, $123,614 profit), continuing the end-of-year dip trend.

###### Key Insight
- Revenue fluctuated within a narrow band of $2.58M–$2.68M, showing strong operational stability. Profit margins remained consistently close to 60%, reflecting disciplined cost management and stable pricing strategy.
- Across all five years, May consistently emerged as the strongest month for both revenue and profit, while February and November repeatedly showed lower sales, highlighting predictable seasonal dips. Despite these monthly fluctuations, the variation is modest, reinforcing the business’s stable operational performance.

### 👥 Customer Insights | page 2
![image](https://github.com/user-attachments/assets/6893a706-cf7a-4ba4-b4a7-32e5e47c3606)

The Customer Insights page explores who is driving revenue in the fashion retail business, highlighting patterns in customer loyalty, gender preferences, age group behavior, and geographic distribution across the 2020–2024 period.

##### Questions answered 
- How many total unique customers made purchases during the period from 2020-2024?
- What is the average spending per customer?
- Repeat customer rate % and revenue from guest % from?
- What percentage of revenue comes from registered vs guest customers?
- Which age groups and gender segments drive the highest sales contribution?
- How is revenue distributed across major cities?

###### Key performance indicators (KPI’s):
Total unique customers: 25k
Average spend per customer: $525.3
Repeat customer Rate%: 56.83%
Revenue from guest %: 3.66%

###### Loyalty: Registered vs Guest Customers
Registered customers overwhelmingly dominate revenue generation throughout the period.
- Registered customers: ~96.9% – 96.93% of total revenue
- Guest customers: ~3.37% – 4.1% of total revenue
This indicates that the business relies heavily on returning customers rather than one-time purchases, suggesting strong brand trust and an effective customer retention strategy.

###### Gender Preferences
Purchasing patterns show a slight but consistent male skew.
- Male revenue share: 50.55% – 51.64%
- Female revenue share: 48.56% – 49.45%
Although the gap is small, male customers consistently generated slightly more revenue across all years.

###### Revenue by Age Group
Customer spending varies significantly across age groups, with clear leaders emerging each year.
- 2020: 35–44 age group generated the highest revenue
- 2021: 55–64 age group led sales
- 2022: 25–34 age group led sales
- 2023: 35–44 age group led sales
- 2024: 45–54 age group generated the highest revenue

Across the entire period, the strongest-performing age segments were 25–54, with the following groups consistently generating over $2 million in cumulative revenue:
- 25–34
- 35–44
- 45–54
- 55–64

Lower-performing segments included:
- 18–24
- 65+

Both remained below $2 million in total revenue, while under-18 customers contributed the least, generating well under $1 million across the five-year period.
This pattern shows that the retailer’s core customer base is concentrated among young professionals and middle-aged shoppers, while younger teens and seniors contribute significantly less to total sales.
