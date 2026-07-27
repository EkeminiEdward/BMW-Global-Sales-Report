# BMW Global Sales Report

---

## ⚙️ Project Type Flags

-  Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
-  Dashboard / Data Visualization
-  Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
-  Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Data Model & Schema](#6-data-model--schema)
7. [Analysis & Metrics](#7-analysis--metrics)
8. [Key Insights](#8-key-insights)
9. [Recommendations](#9-recommendations)
10. [Assumptions & Limitations](#10-assumptions--limitations)
11. [Future Enhancements](#11-future-enhancements)
12. [Deliverables](#12-deliverables)
13. [Author](#13-author)

---

## 1. Project Overview


**Context:** BMW, which is a large-size global premium automotive company, was experiencing inconsistent revenue across its regional markets but couldn't identify the root cause. Also, they want to know how EV adoption trend is at every region, what drives customer satisfaction, how the financing type correlates with vehicle model segments, etc. This project explored 24 months of transactional data across seven regions, with 10,000 premium vehicle transactions, covering 25 countries to determine BMWW's product portfolio, regional sales performance, electric vehicle adoption, pricing strategies, finanacing patterns, warranty packages adoption, customer satifaction, delivery performance, and customer retention.

**Problem Statement:** The dashboard is designed to answer the following stategic questions
                       How is BMW's electric vehicle lineup gaining ground year over year?
                       Do customers in the Middle East pay more than those in Europe?
                       Which models get the deepest discounts, and why?
                       Cash, lease, or loan? How does financing choice correlate with model segment?
                       Customer satisfaction drivers — What predicts a 5-star score vs a 3-star score?
                       Repeat customer analysis — Which segments retain buyers and which ones don't?
                       Delivery time bottlenecks — Does a longer wait hurt satisfaction?

**Approach:** The approach was concise and direct. Started with haveing a proper understanding of the business problem statement, then proceeded to understand the dataset, then performed a rubost and detailed data preparation, modelled the data with a star schema, performed analysis, did evaluations on the analysis, developed an interactive dashboard, provided a high level business recommendations, and finally did a proper documentation.

**Outcome:** Implementation of this dashboard will deliver the following outcomes; improved executive visibility across global operations, faster access to strategic business insights, more informed pricing decisons, better allocation of regional sales resources, increased understanding of customer purchasing behaviour, improved monitoring of customer satisfaction, enhanced identification of revenue growth opportunities, and stronger support for long term strategic planning. 

---

## 2. Objectives


The primary objective of this project is to design an Executive Business Intelligence Dashboard capable of supporting strategic decision-making through comprehensive sales and customer analytics. 
Specifically, the dashboard aims to:
-  Monitor overall business performance using executive KPI indicators.
-  Evaluate revenue performance across reegions, countries, vehicle models, and product segments.
-  Analyze year-over-year sales growth and monthly sales trends.
-  Measure the adoption of BMW's electric vehicle portfolio.
-  Evaluate pricing strategies through discount and revenue analysis.
-  Assess customer satisfaction and identify its primary drivers.
-  Measure customer loyalty using repeat purchase analysis.
-  Analyze financing preferences across customer and product segments.
-  Monitor delivery lead times and evaluate operational efficiency.
-  Enable executives to explore business performance interactively through dynamic filtering and drill-down analysis.


---

## 3. Project Scope & Tools

### Scope


| Dimension | Details |
|-----------|---------|
| **In Scope** | This project includes 10,000 simulated BMW vehicle transactions recorded between January 2024 and December 2025 across more than 25 countries and seven global regions. Analysis covers sales performance, revenue, product performance evaluation, regional performance, customer behaviour, premium warranty adoption, financing, delivery performance, electric vehicle adoption, interactive dashboard development, and strategic business recommendations. |
| **Out of Scope** | The project does not include manufacturing operations, supply chain management, inventory optimization, dealer profitability analysis, marketing campaign effectiveness, vehicle production planning, financial accounting, Cost of Goods Sold(COGS), net profit analysis, and competitor benchmarking. |
| **Time Period** | January 2024 - December 2025 |

### Tools & Technologies

  
| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | CSV files |
| Data Processing | Power Query |
| Analysis | DAX |
| Visualization | Power BI |
| Version Control | Git / GitHub |
| Documentation | Markdown |

---

## 4. Repository Structure

```
BMW-Global-Sales-Report/
│
│── README.md
│
├── Dashboard/
│   ├── BMW_Global_Sales_Report.pbix
│
├── dataset/
│   ├── BMW_Sales_2024_2025.csv               
│
├── visuals/                  
│   ├── Executive_Overview.png
│   ├── Product_Performance.png
│   ├── Customer_Insights.png
│   ├── Regional_Insights.png
│
│__ Assets/
    │__ Dashboard_GIF.gif                  
    │__ Data_Model_architectural_design.png

```

---

## 5. Data Workflow

```
[Data Source(s)]
      ↓
[Ingestion / Collection Method]
      ↓
[Cleaning & Transformation]
      ↓
[Analysis / Modelling / Querying]
      ↓
[Output / Visualisation / Reporting]
```

---

1. **Source:** The dataset contains a CSV file, which is a simulated BMW automotive global sales transactions across seven regions and more than 25 countries, with 10,000 transactional records, covering January 2024 - December 2025.
2. **Ingestion:** Loaded into Power Query. File contained approx. 10,000 rows and 30 columns.
3. **Cleaning:** The dataset was evaluated for missing values across all columns. Expected null values were retained where they accurately represented business scenarios. For example, the loan_term_months column had blank rows for cash purchases because no financing agreements exits. Also, customer_satisfaction_score column is blank for customers who did not complete the post-purchase survey. These null values were preserved to avoid introducing analytical bias. Unexpected null values were investigated and resolved before modelling. Duplicates were checked and removed to ensure that revenue, sales volume, and customer metrics are not overstated. Standardized data formats across the entire dataset. 
4. **Transformation:** Created a dedicated Date table for trend and time intelligence analysis. Created dimension tables for data modelling. Aggregated data to monthly, quaterly, and anually regional gains for trend analysis. Optimized columns for reporting performance.                   
5. **Analysis:** Descriptive statistics, regional comparisons, EV adoption rate, customer satisfaction index (CSI), customer retention rate, top revenue region, top selling model, premium warranty adoption rate, top CSI region, avg delivery lead time, largest EV market, etc.
6. **Output:** Summary report (PDF)

---

## 6. Data Model & Schema


### Dataset / Table: `Transaction_Fact`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `transaction_id` | string | Unique identifier for each sales transaction | BMW-2024-00113 |
| `sale_date` | date | Date the vehicle was sold | Wednesday, January 17, 2024 |
| `sale_year` | int | Year of sale | 2024 |
| `sale_month` | int | Month of sale | 1 (January) |
| `sale_quarter` | string | Fiscal quarter of the transaction | Q1 |
| `model` | string | BMW vehicle model sold | X5 |
| `variant` | string | Specific engine/drivetrain variant | xDrive40i |
| `segment` | string | Vehicle market segment | SUV |
| `body_style` | string | Vehicle body configuration | SUV |
| `fuel_type` | string | Vehicle powertrain | Electric (BEV) |
| `transmission` | string | Transmission type | Automatic |
| `color` | string | Exterior paint colour | Alpine White |
| `trim_line` | string | Vehicle equipment specification | M Sport |
| `optional_packages` | int | Number of optional packages selected | 3 |
| `options_cost_usd` | decimal | Cost of optional equipment | $5,800 |
| `msrp_usd` | currency | Manufacturer's Suggested Retail Price | $82,000 |
| `discount_percent` | decimal(%) | Discount applied to MSRP | 7.5% |
| `discount_amount_usd` | currency | Monetary value of discount | $6,150 |
| `final_sale_price_usd` | currency | Final selling price after discount and options | $81,650 |
| `financing_type` | string | Customer payment method | Lease |
| `loan_term_months` | int | Financing duration | 48 Months |
| `region` | string | Geographic  sales region | Europe |
| `country` | string | Country where vehicle was sold | Germany |
| `sales_channel` | string | Sales channel used | Dealership |
| `customer_type` | string | Buyer classification | Individual |
| `warranty_package` | string | Warranty selected | 5-Year Premium |
| `delivery_days` | int | Days between order confirmation and delivery | 24 Days |
| `customer_satisfaction_score` | decimal | Customer satisfaction rating (1-5) | 4.8 |
| `is_repeat_customer` | boolean | Indicates previous BMW ownership | True |
| `trade_in` | boolean | Indicates whether an existing vehicle was traded in | True |
| `vehicle_id` | string | Unique vehicle identifier | 1 |
| `customer_id` | string | Unique customer identifier | 1 |
| `finance_id` | string | Unique financing type identifier | 1 |
| `geography_id` | string | Unique geographic identifier | 1 |


### Dataset / Table: `Dimn_Customer`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `customer_id` | string | Unique customer identifier | 1 |
| `customer_type` | string | Buyer classification | Individual |
| `warranty_package` | string | Warranty selected | 5-Year Premium |
| `is_repeat_customer` | boolean | Indicates previous BMW ownership | True |


### Dataset / Table: `Dimn_Finance`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `finance_id` | string | Unique financing type identifier | 1 |
| `financing_type` | string | Customer payment method | Lease |
| `loan_term_months` | int | Financing duration | 48 Months |


### Dataset / Table: `Dimn_Geography`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `geography_id` | string | Unique geographic identifier | 1 |
| `region` | string | Geographic  sales region | Europe |
| `country` | string | Country where vehicle was sold | Germany |


### Dataset / Table: `Dimn_Vehicle`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `vehicle_id` | string | Unique vehicle identifier | 1 |
| `model` | string | BMW vehicle model sold | X5 |
| `variant` | string | Specific engine/drivetrain variant | xDrive40i |
| `segment` | string | Vehicle market segment | SUV |
| `body_style` | string | Vehicle body configuration | SUV |
| `fuel_type` | string | Vehicle powertrain | Electric (BEV) |
| `transmission` | string | Transmission type | Automatic |
| `color` | string | Exterior paint colour | Alpine White |
| `trim_line` | string | Vehicle equipment specification | M Sport |
> **Row count (approx.):** 10,000
> **Date range:** Monday, January 1, 2024 – Wednesday, December 31, 2025
> **Key join / relationship:** `Dim_Customer.customer_id` → `Transaction_Fact.customers_id`, `Dim_Finance.finance_id` → `Transaction_Fact.finance_id`, `Dim_Geography.geography_id` → `Transaction_Fact.geograhy_id`, `Dim_Vehicle.vehicle_id` → `Transaction_Fact.vehicle_id` (ALL: One-to-Many Single Direction Relationships)

---

## 7. Analysis & Metrics


### Analytical Approach

This project adopted a descriptive statistical analysis and trend analysis approach using a dimensional (star schema) data model, Power Query for data transformation, and DAX  measures to evaluate slaes performance, pricing, customer behaviour, regional performance, and operational efficiency. Interactive Power BI visualizations, time intelligence, and comparative analyses were then used to reveal business insights, identify performance drivers, and support executive-level strategic decision-making.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `Revenue` | Total revenue realised after discounts and options | Actual commercial revenue |
| `Vehicle Sold` | Total number of completed vehicle sales | Sales volume |
| `Gross MSRP` | Total Manufacturer's Suggested Retail Price before discounts | Potential sale value |
| `Total Discounts` | Total discount value granted | Discount expenditure |
| `Avg Selling Price` | Average selling price per vehicle | Revenue quality |
| `Avg Discount Rate ` | Average percentage discount offered | Pricing strategy effectiveness |
| `Revenue YTD` | Revenue accumulated from the beginning of the year | Year-To-Date performance |
| `Revenue LY` | Revenue for the saame period in the previous year | Historical comparison |
| `Revenue YoY Rate` | Percentage revenue growth over previous year | Growth rate |
| `Top Selling Model` | Model with the highest sale volume | Product demand |
| `Top Revenue Model` | Model generating the highest revenue | Product profitability potential |
| `EV Adoption Rate` | Percentage of vehicles sold that are electric vehicles | Electrification progress |
| `Largest EV Market` | Region with the highest EV sales | Leading EV market |
| `PW Adoption Rate` | Percentage of customers selecting the premium warranty | After-sales service adoption |
| `Customer Retention Rate` | Percentage of repeat customers | Customer loyalty |
| `Customer Satisfaction Index (CSI)` | Average customer satisfaction score | Customer experience |
| `Top Revenue Region` | Region generaating the highest revenue | Best-performing market |
| `Top CSI Region` | Region with the highest satisfaction score | Best customer experience |
| `Avg Lead Time` | Average number of days required to deliver a vehicle | Operational efficiency |



### Methods Used

- Data Cleaning and Transformation (Power Query ETL).
- Created a Dimensional Data Modelling (Star Schema).
- DAX Measure Development.
- Descriptive statistics - distribution analysis, comparative data analysis.
- Time intelligence and Trend analysis across January, 2024 - December, 2025.
- Interactive Data Visualization and Executive Dashboard Design

---

## 8. Key Insights


**Insight 1: BMW commercial performance across global markets**
The executive overview page portrays key commercial indicators including Revenue, Vehicle Sold, Gross MSRP, Total Discount, Revenue Trends, and Revenue Growth. Revenue Trends reveal seasonal demand fluctuations while highlighting overall commercial performance throughout the reporting period.

**Insight 2: Regions that generate the greatest commercial value**
Regional analysis compaqres total revenue, sales volume, customer satisfaction, and delivery performance across all global markets.
Comparative visuals clearly identify high-performing regions and markets requiring strategic interveention. North America had the highest revenue (approx. $177M), Europe had the highest sales volume (2919 vehicles sold) throughout the reporting period.

**Insight 3: BMW  models that generate the highest business value**
Product performance analysis evaluates each model using both revenue and sales volume. The distinction between Top Selling Model and Top Revenue Model enables management to differentiate between popularity and profitability. 3 Series was the Top Selling Model, and X5 was the Top Revenue Model throghout the reporting period.

**Insight 4: Is BMW's electric vehicle strategy gaining market traction?**
Electric vehicle adoption was measured using Fuel Type analysis, EV A doption Rate, and Largest EV Market. Regional comparisons revealed where BMW's electrification strategy has achieved the greatest commercial success. The EV market grew in revenue from $37M in year 2024 to the revenue of $38M in year 2025. North America is the region with the largest EV market, with a sales volume of 342 vehicles sold across the reporting period.

**Insight 5: Customer Satisfaction Index**
Customer Satisfaction Index (CSI) is analysed by region, model, and delivery performance. The analysis identifies geographic differences in customer experience and highlights factors influencing post-purchase satisfaction. In the report, Rental customers in the Latin America region, were the most satisfied customers with a satisfaction score of 4.55, while the African Government customers were the least satisfied customers, with a score of 3.85.

**Insight 5: Does delivery performance inluence customer satisfaction?**
Operational performance is assessed by comparing Average Delivery Lead Time with Customer Satisfaction Index. The scatter analysis reveals whether longer delivery times correspond with lower satisfaction levels. In the report, it revealed that the average delivery lead time did influence the customer satisfaction, because all the regions were satisfied with the delivery lead time.

**Insight 6: Regions to be prioritized for future growth**
Region-level revenue rankings, orevenue contribution, and EV adoption metrics identify markets with the greatest expansion potential. The analysis enables executives to distinguish mature markets from emerging opportunities. North America and Europe, returned as the top revenue regions and highest in EV adoption rate, which suggests and supports market expansion. on the contrary, Africa was the lowest region in revenue and EV adoption, which calls for an executive investment planning.

---

## 9. Recommendations


| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Expand Investment in High-Performing Markets; Increase inventory allocation for high-demand markets, expand dealership capacity where demand consistently exceeds supply, prioritize premium model availability, and allocate  a greater share of regional marketing budgets to sustain momentum. | Business Insight 2 - Region that generates the greates commercial value. | Executives |
| Medium | Strnghten Underperforming Regional Markets; Conduct market-specific pricing reviews,assess dealership coverage and customer accessibility, increase localized promotional campaigns, and introduce region-specific financing incentives where appropriate | Business Insight 2 | Executives |
| Medium | Prioritize High-Value Product Lines; Increase production and availability of high-revenue model, use best-selling models as customer acquisition vehicles while promoting premium variants through upselling, and review product portfolio performance quarterly to identify changing demand patterns. | Business Insight 3 - BMW models that generate the highest business value | Executives |
| High | Accelerate Electric Vehicle Growth; Expand EV inventory in markets demonstrating strong adoption, increase partnerships supporting charging infastructure where feasible, develop targeted campaigns highlighting total cost of ownership and sustainability benefits, and introduce tailored financing packages for electric vehicles. | Business Insight 4 - Is BMW's electric vehicle strategy gaining traction? | Executives |
| High | Improve Customer Experience Through Delivery Optimisation; Investigate operational bottlenecks affecting vehicle delivery, improve coordination between production, logistics, and dealerships, implement delivery performance monitoring dashboards for regional managers, and establish lead-time targets and track adherence monthly. | Business Insight 5 - Does delivery performance influence customer satisfaction? | Executives |
| Ongoing | Institutionalise Data-Driven Deciosn-Making; Adopt a dashboard as the primary source for executive performance reporting, standardise KPI definitions across departments, schedule periodic reviews of business metrics and DAX logic to ensure continued alignment with evolving business objectives, and extend the dashboard with additional subject areas, such as inventory, dealer performance, and after-sales service, as new data becomes available. | All Business Insights | Executives |

---

## 10. Assumptions & Limitations


### Assumptions
The solution assumes:
- Each transaction represents one completed vehicle sale.
- Transaction IDs are unique.
- Data is complete and internally consistent.
- Vehicle delivery dates are accurately recorded.
- Warranty and financing information are correctly captured.

### Limitations
- The dashboard is built using a simulated dataset designed to resemble real-world BMW sales transactions.
- The analysis covers transactions from January 2024 through December 2025, only.
- Revenue calculations are based on Final Sale Price. The dataset does not include; cost of goods sold(COGS), manufacturing costs, logistics costs, dealer incentives, operating expenses, and marketing expenditure.
- Gross Profit, Operating Profit, Profit Margin, and Return on Investment cannot be calculated because the irquired financial data is unavailable.
- Approximately one-quarter of the customer satisfaction scores are unavailable because not every customer completed the post-purchase survey.
- Customer attributes are intentionally limited. Unavailable attributes include; age, gender, household income, occupation, customer tenure, and household size.
- The dataset includes regions and countries only. Unavailable geographic information includes; cities, states or provinces, dealership locations, and sale territories.
- The dataset does not include; vehicle inventory, stock availability, factory production, logistics milestones, and supplier information.
- Marketing metrics are unavailable. Missing information includes; campaigns, advertising spend, lead generation, digital engagement, and conversion funnels.
- All monetary values are reported in USD. Foreign exchange fluctuations are not considered

---

## 11. Future Enhancements


-  Profitability Analttics - Integrate financial data to enable; gross profit, operating profit, net profit, profit margin, cost-to-revenue ratio, profitability by model, and profitability by region.
-  Inventory & Supply Chain Analytics - Expand the model to include; vehicle inventory, inventory turnover, days of supply, factory production, shipment tracking, and stock-out analysis.
-  Service & After-Sales Analytics - Incorporate after-sales data such as; service visits, maintenance costs, warranty claims, parts replacement, and service retention.
-  Marketing Performance Integration - Connect marketing data to measure; campaign performance, lead conversion, customer acquisition cost, return on marketing investment, digital channel performance.
-  Customer 360 Analytics - Enhance customer analysis through additional attributes including; demographics, purchase history, customer lifetime value(CLV), churn risk, and loyalty programme participation.
-  Reat-Time Reporting - Integrate streaming or near real-time data sources to monitor; daily sales, revenue, vehicles deliveries, customer satisfaction, and dealer performance.

---

## 12. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| BMW Global Sales Executive Overview | Contains a high-level view of business performance. | visuals/Executive Overview.png |
| Customer Insights | Focuses on customer behaviour and retention. | visuals/Customer Insights.png |
| Product Performance | Analyzes marketplace performance. | visuals/Product performance.png |
| Regional Insights | Monitors regional business transaction performance. | visuals/Regional Insights.png |
| Data Model | A Star schema data model was implemented | Assets/Data Model architectural design.png |

---

## 13. Author

**Ekemini Edward**
Data Analyst

- 🔗 www.linkedin.com/in/ekemini-edward-052b5157
- 💼 https://github.com/EkeminiEdward/EkeminiEdward.github.io.git
- 📧 edyswagg@gmail.com


---

*Last updated: July 2026*
