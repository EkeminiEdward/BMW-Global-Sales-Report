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
7. [ERD - Entity Relationship Diagram](#7-erd--entity-relationship-diagram) *(SQL projects)*
8. [Analysis & Metrics](#8-analysis--metrics)
9. [Key Insights](#9-key-insights)
10. [Recommendations](#10-recommendations)
11. [Assumptions & Limitations](#11-assumptions--limitations)
12. [Future Enhancements](#12-future-enhancements)
13. [Deliverables](#13-deliverables)
14. [Author](#14-author)

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
[project-root]/
│
├── data/
│   ├── raw/                  # Original, unmodified source data - never edited
│   ├── processed/            # Cleaned and transformed data
│   └── external/             # Reference data, lookup tables, third-party files
│
├── scripts/                  # Reusable .py, .R, or .sh processing files
│
├── reports/                  # Final outputs: PDFs, slide decks, Word docs
│
├── visuals/                  # Exported charts, dashboard screenshots, ERD diagrams
│
├── docs/                     # Data dictionaries, schema notes, reference material
│
└── README.md                 # You are here
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
> **Key join / relationship:** `Dim_Customer.customer_id` → `Transaction_Fact.customers_id`, `Dim_Finance.finance_id` → `Transaction_Fact.finance_id`, `Dim_Geography.geography_id` → `Transaction_Fact.geograhy_id`, `Dim_Vehicle.vehicle_id` → `Transaction_Fact.vehicle_id`
(ALL : One-to-Many Relationship)


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

- Descriptive statistics - distribution analysis.
- Time intelligence and Trend analysis across January, 2024 - December, 2025.
- [e.g., Segmentation / group comparison by [dimension]]
- [e.g., Correlation analysis between [variable A] and [variable B]]
- [e.g., SQL window functions for [specific aggregation]]
- [e.g., Custom aggregation or transformation logic in [tool]]

---

## 8. Key Insights

<!--
  Findings + implications. Not just what happened - what it means.

  WHAT GOOD LOOKS LIKE:
  ✅ "Return rates, not sales volume, explain Region A's underperformance.
      Region A's return rate on home goods was 34% - more than double the
      company average. Revenue was not lost at the point of sale; it was
      lost post-sale through refunds. This points to a fulfilment or
      product quality issue specific to that region, not a demand problem."

  WHAT TO AVOID:
  ❌ "Region A had lower revenue than other regions in Q4."
     (That's an observation. It describes what happened.
      An insight says what it means and where to look next.)

  Aim for 3–6 insights. Quality over quantity.
-->

**Insight 1: [Short descriptive headline]**
[What you found + what it suggests. One short paragraph.]

**Insight 2: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 3: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 4 (if applicable): [Short descriptive headline]**
[What you found + what it suggests.]

---

## 10. Recommendations

<!--
  Action-oriented. Addressed to a real audience.
  Tied explicitly to the insight that supports each one.

  WHAT GOOD LOOKS LIKE:
  Priority: High
  Recommendation: "Conduct a fulfilment audit for home goods deliveries
                   in Region A - specifically investigating whether returns
                   correlate with a particular warehouse, carrier, or SKU batch."
  Based On: Insight 1 - return rate anomaly in Region A
  Owner: Operations / Supply Chain team

  WHAT TO AVOID:
  ❌ "Improve the return rate."
     (Not actionable. Doesn't say who, how, or where to start.)
  ❌ "Further analysis is needed."
     (This is a placeholder, not a recommendation.)
-->

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Medium | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Low | [Exploratory or longer-term suggestion] | [Insight it comes from] | [Who should act] |

---

## 11. Assumptions & Limitations

<!--
  WHAT GOOD LOOKS LIKE:
  Assumption: "Transaction records were assumed to be complete for all five regions.
               No validation was performed against source system record counts."
  Limitation: "The analysis cannot distinguish between returns initiated by
               the customer vs. returns initiated by the business (e.g., recalls).
               If business-initiated returns are concentrated in Region A, the
               return rate finding may reflect a policy decision, not a quality issue."

  WHAT TO AVOID:
  ❌ Leaving this section blank or writing "None known."
     Every project has limitations. Documenting them is a sign of
     analytical maturity - not a confession of failure.
-->

### Assumptions
- [What did you treat as true without being able to verify?]
- [What simplifications did you make for scope or feasibility?]
- [What domain rules or definitions did you accept as given?]

### Limitations
- [What gaps exist in the data?]
- [What analysis was out of scope but could affect interpretation?]
- [What would a more rigorous version of this project include?]
- [Are there known biases in the data source or collection method?]

> *The goal here is pre-emptive Q&A. What would a thoughtful skeptic push back on? Document the answer here, before they ask.*

---

## 12. Future Enhancements

<!--
  WHAT GOOD LOOKS LIKE:
  ✅ "Automate the monthly data pull from the POS export folder using
      a scheduled Python script, replacing the current manual process."
  ✅ "Expand the return rate analysis to include carrier-level data,
      which was unavailable in this dataset but exists in the logistics system."

  WHAT TO AVOID:
  ❌ "Add a machine learning model."
     (Vague, and disconnected from the actual findings of this project.)
  ❌ Listing aspirational features that don't follow logically from the work.
-->

- [ ] [Enhancement 1 - specific and traceable to a real gap in this project]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]
- [ ] [Enhancement 4]

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |

---

## 14. Author

**[Your Name]**
[Your role or title - current or target]

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
