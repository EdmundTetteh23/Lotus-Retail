# Lotus Retail — Sales, Store & Customer Intelligence
An end-to-end retail performance and dynamic analytics solution built for Lotus Retail, transforming raw operational logs into a multi-page interactive Tableau workbook. This project equips business leaders with high-density comparative metrics and regional deep-dives to evaluate year-over-year operational trends across key performance indicators using flexible, parameter-driven visual controls.

## Table of Contents
- [Overview](#overview)
- [Project Brief and Problem Statement](#Project-Brief-and-Problem-Statement)
- [Data Pipeline and Architecture](#Data-Pipeline-and-Architecture)
- [Data Transformation and Cleaning](#Data-Transformation-and-Cleaning)
- [Data Model and Relationships](#Data-Model-and-Relationships)
- [Core DAX Measures and Formulas](#Core-DAX-Measures-and-Formulas)
- [Dashboards and Visualizations](#Dashboards-and-Visualizations)
- [Key Business Insights](#Key-Business-Insights)
- [Strategic Recommendations](#Strategic-Recommendations)
- [Tech Stack](#Tech-Stack)
- Author

## Overview
Lotus Retail required a centralized, multi-dimensional analytical platform to monitor sales trajectory, customer demographics, and store/product efficiency across operating regions. This project establishes a unified business intelligence framework by modeling transactional, return, and inventory records into a flexible relational structure in Tableau, featuring dynamic metric parameters (Cost, Revenue, Profit, and Orders) paired with Year-Over-Year (YoY) benchmarking.

⚙️ Data Pipeline and Architecture

[Raw Dataset] ➔ [Multi-Fact Data Model] ➔ [Calculated Fields & Parameters] ➔ [Interactive Tableau Workbook ]

## Data Model and Relationships
The data architecture utilizes a multi-fact relational data model built directly within Tableau's logical layer, connecting core transactional tables with descriptive lookup dimensions:


- fact_orders: Central order entity capturing customer ID, employee ID, store ID, order date, order status, payment method, and total cost.
- fact_order_details: Itemized order line items linked to fact_orders on order_id, tracking product-level pricing, line revenue, discounts, costs, and unit quantities.
- fact_returns: Return log table capturing refund methods, dates, return reasons, status, and returned amounts linked via order_id.
- dim_customers: Lookup dimension for customer demographic profiles, full names, birth dates, registration dates, gender, and assigned loyalty tiers.
- dim_products: Merchandise details tracking brands, product names, categories, sizes, colors, stock quantities, unit costs, and retail prices.
- dim_stores: Operational store lookup tracking store names, cities, districts, regions, store types (Flagship, Standard, Small), opening years, and square footage.
- dim_employees: HR lookup containing employee names, roles, hire dates, store assignments, and salary attributes.
- dim_date: Date table driving calendar granularity (Year, Month, Day, Day Type, and Ramadan flags).
- dim_orders: table consisting of order_id to connect two fact tables.

## Tableau Calculations & Business Logic
Analytical logic and metric parameter switching implemented via dynamic Tableau Calculated Fields and Dynamic Parameters

<img width="525" height="320" alt="Current Year Cost" src="https://github.com/user-attachments/assets/d14f76bc-a0c1-4f0f-88cf-862bb4554d99" />


<img width="524" height="321" alt="Previous Year Cost" src="https://github.com/user-attachments/assets/0e81e7e0-2aa5-4a8c-a39b-1c7e369b0716" />


<img width="524" height="322" alt="YoY Cost" src="https://github.com/user-attachments/assets/f8e188b1-e536-49b7-955d-5e31d13e8de4" />


<img width="525" height="322" alt="Metric Current Year" src="https://github.com/user-attachments/assets/eab292ad-1df3-4e65-afe1-5e69c73ee616" />


<img width="523" height="320" alt="Metric Previous Year" src="https://github.com/user-attachments/assets/ed852d48-1f8b-4f90-afdc-709426fcf404" />


<img width="525" height="321" alt="Metric YoY" src="https://github.com/user-attachments/assets/47d3003c-91ba-4af5-a12a-4f65d6710b2d" />


- Dynamic Metric Selection: Uses dynamic parameter controls to allow the entire dashboard user interface (charts, bar segments, ranking lists) to instantly switch measure context across Revenue, Cost, Profit, and Orders.
- Time Intelligence & Comparative Modeling: Employs level-of-detail (LOD) expressions and table calculations to compute Previous Year (PY) baselines for every metric, rendering real-time target indicator lines and percentage variance comparisons (% vs PY).
- Core KPI Aggregations: Calculated measures computing cumulative totals, profit margins, distinct customer counts (COUNTD), total orders, and average order values.

## Dashboards and Visualizations
### Dashboard 1 — General Overview
Provides executive visibility into enterprise-wide financial health and operational timing dynamics.

Executive KPI Header: Total Cost (E£12.3M, +8.2% vs PY), Total Revenue (E£15.6M, +7.3% vs PY), Total Profit (E£3.3M, +4.1% vs PY), and Total Orders (4.1K, +1.8% vs PY).

Dynamic Time Trends: Monthly metric trend area chart paired with day-of-week and weekday/weekend performance breakdowns featuring previous-year benchmark lines.

Historical Benchmarks: Comparative bar charts tracking year-by-year trajectory (2022–2024) across all core metrics.

Dashboard 2 — Customer Analysis
Focuses on customer lifetime value, demographic behavior, registration velocity, and loyalty segmentation.

Demographic Distributions: Comparative bar charts breaking down selected metrics across customer age bins (20–29, 30–39, 40–49, 50–59) and registration years (2020–2023).

Loyalty & Customer Type: Donut chart detailing customer mix (97% Returning vs. 3% One-Time) alongside horizontal breakdowns across Loyalty Tiers (Bronze, Silver, Gold, Platinum).

Customer Leaderboard: Dynamic top-N ranking visual identifying high-value individual customer accounts.

Dashboard 3 — Store & Product Analysis
Evaluates physical retail footprint efficiency, regional density, and merchandise performance.

Store Footprint KPIs: High-level counters tracking active store locations (15 stores) and product line depth (62 active products).

Geographic & Channel Breakdown: Metric performance ranked by operating Region (led by Cairo and Alexandria) and Store Type (Flagship, Standard, Small).

Merchandise Intelligence: Ranked horizontal bar charts displaying Top 10 Brands, Top 10 Products, and Bottom 10 Products by performance.

📈 Key Business Insights

Financial & Performance Trends

Solid Financial Growth: Lotus Retail recorded E£15.6M in Total Revenue and E£3.3M in Total Profit in 2024, achieving positive YoY growth across all primary metrics (+7.3% Revenue, +4.1% Profit).

Cost Expansion Outpacing Profit Growth: Total Cost increased by 8.2% YoY (reaching E£12.3M), rising slightly faster than revenue (+7.3%), signaling slight margin compression due to operational cost pressures.

Weekday Dominance: Weekdays generate the vast majority of business activity (E£11.8M Revenue / 2.99K Orders) compared to weekends (E£3.8M Revenue / 1.06K Orders), with Monday and Sunday representing peak individual days.

Customer Demographics & Retention

High Retention Base: The customer base is exceptionally loyal, with 97% (2,166) classified as returning customers versus only 3% (77) one-time buyers.

Core Purchasing Demographics: Customers aged 30–49 represent the revenue engine of the business, generating E£9.7M (~62%) of total revenue (E£4.8M from 30–39 and E£4.9M from 40–49).

Loyalty Tier Concentration: Bronze tier members make up 52% of total customers (1,184) and drive the largest volume (E£7.6M Revenue), while Platinum members (4% of user base) present significant upsell potential.

Store Footprint & Brand Performance

Regional Dominance: Cairo is the top-performing market by a wide margin (E£3.0M Cost/Revenue driver), followed by Alexandria (E£1.5M), while smaller regions like Luxor and Aswan remain underutilized.

Flagship Efficiency: Flagship store formats generate the highest revenue density (E£4.5M), followed closely by Standard stores (E£4.2M).

Brand Velocity: Nile Fashion (E£5.0M) and Delta Wear (E£4.0M) lead overall brand performance, while tech accessories (routers, power banks) represent the bottom performing product tier.

💡 Strategic Recommendations

Optimize Cost Structure in High-Volume Regions: Conduct a margin audit on store operations in Cairo and Alexandria to slow cost growth (+8.2% YoY) and bring expenditure growth in line with revenue expansion.

Capitalize on Core Demographics: Design targeted promotional campaigns around the 30–49 age segment and create tier-transition incentives to migrate Bronze loyalty members (52% of base) into Silver and Gold tiers.

Refine Product Assortment: Evaluate low-performing SKU categories in the bottom 10 products list (e.g., lower-margin tech accessories) to clear unproductive inventory and reallocate shelf space to top apparel brands like Nile Fashion and Delta Wear.

Target Weekend Footfall Strategy: Introduce weekend-only promotional bundles or events to activate weekend retail traffic, bridging the gap between weekday volume (E£11.8M) and weekend sales (E£3.8M).

🛠️ Tech Stack

Data Source: Enterprise Retail Transactional Files & Dimensions

Data Modeling: Multi-Fact Relational Layer (Logical Relationships)

Calculations & Metrics: Tableau Calculated Fields, Dynamic Parameters, LOD Expressions, Table Calculations

Visualization: Tableau Desktop / Tableau Cloud
