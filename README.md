# Fashion Retail Sales Insights | Data Modeling, DAX & Performance Insights (2020–2024)

## Table Of Contents
[Project Overview](#project-overview)

[Process](#process)

###### Project Insights:
[📊 Sales Overview | page 1](#-sales-overview--page-1)

[👥 Customer Insights | page 2](#-customer-insights--page-2)

[🛍️ Product performance | page 3](#-product-performance--page-3)

[🏬 Store performance | page 4](#-store-performance--page-4)


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

###### Revenue by City
Revenue is well distributed across major cities, indicating strong geographic coverage.
- Lisbon led revenue from 2020 to 2023
- Porto became the top-performing city in 2024.

Despite these leadership changes, overall city performance remained very close. Across the five-year period:
- Lisbon
- Faro
- Braga
- Coimbra
- Porto

all generated total revenue within a narrow range of $2.44M to $2.61M.

###### 🔎 Key Insights
- The business relies heavily on registered customers, with nearly 97% of revenue coming from repeat buyers, highlighting strong customer loyalty.
- Customers aged 25–54 represent the core market segment, consistently generating the majority of revenue across the five-year period.
- Male customers contribute slightly more revenue than female customers, though the difference remains relatively small.
- Revenue is evenly distributed across major cities, suggesting stable demand across locations rather than dependence on a single market.

#### 🛍️ Product performance | page 3
![image](https://github.com/user-attachments/assets/cc00d9ec-134c-4589-a720-0fca9f54c3b0)

Product Performance analysis examines how different product categories, seasonal trends, suppliers, and product variations (size and color) contributed to overall revenue between 2020 and 2024.

##### Questions answered
- What is the total products purchased from 2020-2024?
- What is the total cost of products purchased ?
- How many orders were returned from 2020-2024?
- Which product categories generate the strongest revenue and profit?
- Is demand concentrated in specific category–size–color combinations?
- How balanced is supplier contribution, and is there overreliance on any vendor?
- Which season generates more sales?

###### Key performance indicators (KPIs)
Total products: 50k
Total cost: $5.31M
Returned orders: 5k
Total revenue: $13M
Profit margin: 59.72%

###### Sales by category:

Over the five-year period:
- Tops generated the highest total revenue at approximately $2.63M
- Accessories followed closely with $2.63M
- Shoes generated $2.61M
- Dresses contributed about $2.58M
- Bottoms recorded $2.57M

The difference between the highest and lowest category revenue is relatively small (around $64K), indicating that the product catalog performs consistently across categories rather than relying heavily on a single product line.
###### Profit Contribution by Category:
Profit distribution mirrors the revenue trend, showing a balanced contribution across categories.

Over the five-year period:
- Shoes generated the highest total profit at approximately $1.57M
- Tops followed closely with about $1.56M
- Accessories contributed roughly $1.56M
- Dresses produced around $1.53M
- Bottoms generated about $1.53M

Profit margins remain remarkably consistent across categories, suggesting the company maintains stable pricing strategies and effective cost control across its product lines.

From the yearly breakdown:
- 2023 recorded the highest overall revenue and profit across most categories, making it the strongest year for product performance.
- 2021 experienced a slight dip in revenue across several categories, particularly in Tops and Bottoms.
- Revenue rebounded steadily from 2022 onwards, with most categories maintaining stable growth through 2024.

Despite minor fluctuations, the product portfolio demonstrates consistent year-to-year stability, reinforcing the strength of the brand’s product mix.

###### Sales by season:
Seasonal performance shows that revenue is evenly distributed across the four seasons,
Over the full period:
- Summer generated the highest cumulative revenue at $3.30M
- Winter followed extremely closely at $3.29M
- Spring recorded $3.27M
- Fall generated $3.26M

The difference between the highest and lowest season is less than $40K, which is very small relative to the $13.13M total revenue.

Year-by-year patterns show that:
- Spring led in 2020, generating the strongest seasonal revenue.
- Summer dominated 2021 and 2022, showing consistent demand during warmer months.
- Summer remained the top performer again in 2023, contributing to the overall peak year for the business.
- Winter slightly overtook other seasons in 2024, recording the strongest revenue that year.

###### Supplier performance :
Totals (2020–2024):
- Supplier D → ~$3.30M (highest overall)
- Supplier B → ~$3.29M
- Supplier A → ~$3.28M
- Supplier C → ~$3.26M 

Revenue contribution across suppliers remains highly balanced over the five-year period, with minimal concentration risk.
Supplier D leads overall contribution, closely followed by Suppliers B and A, while Supplier C trails slightly. However, the revenue gap between the highest and lowest supplier is marginal, indicating a diversified sourcing structure rather than dependency on a single vendor.

Year-to-year fluctuations are present but not structural. For example:
- Supplier B peaked strongly in 2023.
- Supplier A showed consistent stability across all five years.
- Supplier D experienced a dip in 2021 before recovering in subsequent years.


###### Revenue across category–size–color :
combinations shows moderate variation, with the highest-performing combination reaching approximately $102k and the lowest around $67k. Gap = about $35,775
The relatively narrow gap suggests demand is distributed across multiple product variations rather than concentrated in a single dominant combination.

###### Key Insights
- Product revenue is evenly distributed across categories, with Tops, Accessories, and Shoes slightly outperforming other categories. The small gap between the highest and lowest performing category suggests that the retailer benefits from a well-balanced product portfolio rather than relying on a single product line.
- Shoes generated the highest overall profit, indicating that this category may offer slightly stronger margins compared to other products, making it an important contributor to overall profitability.
- Seasonal demand remains stable across all four seasons, with Summer and Winter showing marginally stronger performance. The minimal variation between seasonal sales suggests that the retailer experiences consistent year-round demand rather than heavy seasonal dependency.
- Supplier sales contributions appear relatively balanced, indicating that the business is not overly dependent on a single supplier. This helps reduce supply chain risk and ensures product availability across categories.
- Across most product dimensions—category, season, size, and color—sales patterns remain highly consistent, indicating a diversified product strategy and stable consumer demand.

### 🏬 Store performance | page 4
![image](https://github.com/user-attachments/assets/0f8ea9ff-8d21-42e9-b851-947731ed3254)

The Store Performance page evaluates how different regions, store locations, and store sizes contributed to revenue and profitability between 2020 and 2024. The analysis highlights geographic performance patterns, store-level leaders, and whether store size influences sales outcomes.

##### Questions answered 
- Whats the average revenue per store?
- How many stores are in total?
- which stores are doing best?
- Does store size influence revenue performance?
- Which regions and store locations contribute most to total revenue?

###### Key performance indicators(KPIs)
Total stores: 5
Avg revenue per store: $2.63M
Total Revenue: $13M
Profit margin: 59.27%

###### Sales and Profit by Store:
At the individual store level, performance remains similarly balanced.

Top-performing stores by total revenue:
	1.	Faro Outlet → $2.65M revenue | $1.59M profit
	2.	Lisbon Flagship → $2.65M revenue | $1.58M profit
	3.	Coimbra Boutique → $2.60M revenue | $1.55M profit
	4.	Online Store → $2.58M revenue | $1.54M profit
	5.	Porto Center → $2.58M revenue | $1.54M profit

Faro Outlet and Lisbon Flagship lead overall performance, though the revenue difference between the highest and lowest store is only about $73K, indicating a well-balanced store network.
Profit margins remained consistently strong across all stores, averaging approximately 59.57%, reflecting effective cost management regardless of location.

Year by year patterns shows that:
- 2023 recorded the strongest overall performance, with most stores reaching their highest revenue and profit levels.
- 2024 showed a slight moderation, particularly for the Online and Lisbon Flagship stores.
- 2020–2022 remained relatively stable, with small fluctuations but no major declines.

The Online store experienced its strongest year in 2023, generating approximately $555K in revenue, before declining slightly in 2024.

###### Store size performance :
Smaller stores win on total revenue The 179 m² and 238 m² stores generated the highest cumulative revenue (~$2.65M each), tying or very close to the 336 m² group. Larger stores (728 m² and 950 m²) fell behind, with totals around $2.58M–$2.60M.

Consistency across years Smaller sizes (179–336 m²) outperformed larger ones in every single year from 2020 to 2024. The gap was small in some years, but the pattern never reversed.

Efficiency insight Smaller stores likely achieve higher revenue per square meter (a key retail KPI). For example:
179 m² store → ~$14,830 per m² total
950 m² store → ~$2,741 per m² total → Small stores are 5–6× more efficient per square meter of space.

###### Store by region indicates: 
- Algarve → $2.65M
- Lisbon → $2.65M
- Coimbra → $2.60M
- Online → $2.58M
- Porto → $2.58M

Algarve and Lisbon emerge as the top-performing regions, each generating approximately $2.65M in cumulative revenue between 2020 and 2024. Coimbra follows closely with about $2.60M, while Porto and Online sales each contributed roughly $2.58M which is relatively narrow. This indicates a geographically diversified revenue base rather than dependency on a single high-performing market.

That gap from highest to lowest?
Roughly $73k across five years. Revenue contribution across regions remains highly balanced over the five-year period, with minimal variation between top and bottom performers.
Year-to-year fluctuations exist (such as stronger Online performance in 2023), but no region shows structural decline or dominance.

Overall, regional sales distribution reflects stable demand across physical locations and digital channels, reducing geographic concentration risk and reinforcing the business’s balanced market presence.

###### Key Insights
- Revenue is evenly distributed across regions, with Algarve and Lisbon only marginally ahead of Coimbra, Porto, and Online sales. This indicates the business is not overly dependent on a single geographic market.
- Faro Outlet and Lisbon Flagship slightly outperform other stores, but the overall revenue gap between the highest and lowest-performing store is relatively small (about $73K), reflecting a balanced store portfolio.
- 2023 was the strongest year for most stores, aligning with the overall company-wide revenue peak observed in the sales performance analysis.
- Profit margins remain highly consistent across all stores (around 59%), suggesting strong operational control and stable pricing strategies.
- Smaller store formats appear to outperform larger ones, indicating that location efficiency and customer traffic may drive performance more than store size alone.

### Strategic Recommendations

The analysis highlights several patterns that the business could explore to further optimize performance.

1. Capitalize on High-Performing Months
Sales trends show that May consistently records the strongest revenue and profit, while months such as February and November tend to be slightly weaker.
The company could consider aligning marketing campaigns, promotions, or product launches around these seasonal patterns to maximize demand during peak periods and stimulate sales during slower months.

2. Encourage Conversion of Guest Shoppers
Although guest purchases represent only a small share of revenue (around 3–4%), converting these shoppers into registered customers could provide additional long-term value. Encouraging account creation during checkout or offering small loyalty incentives may help increase repeat purchases and improve customer tracking.

3. Focus on Core Revenue-Driving Demographics
Customers between the ages of 25 and 54 consistently contribute the largest share of revenue. This suggests that product offerings and marketing efforts aligned with this demographic could have the greatest impact on future sales growth.

4. Maintain a Diversified Product Mix
Revenue and profit are distributed fairly evenly across product categories, with Tops, Accessories, and Shoes slightly leading overall performance. This balanced distribution indicates that the retailer benefits from a diversified catalog, which helps reduce reliance on a single product category.

5. Evaluate Store Format Efficiency
Store analysis shows that smaller stores tend to generate higher revenue per square meter compared to larger locations. While overall store performance remains balanced, this pattern suggests that compact retail formats may offer better space efficiency and could be considered when evaluating future store expansion strategies.
