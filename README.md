# Fashion Retail Sales Insights | Data Modeling, DAX & Performance Insights (2020–2024)

## Table Of Contents




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

#### 📊 Sales Overview (Financial performance) (page 1)
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
