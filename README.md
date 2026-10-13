# Retail Inventory & Supply Chain Analytics

**Power BI Portfolio Project | Inventory Optimization · ABC/Pareto Analysis · Profitability · Procurement Intelligence · Replenishment Planning**

An end-to-end business intelligence project designed to transform retail inventory data into actionable insights for inventory control, purchasing decisions, supplier analysis, and commercial performance evaluation.

[![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/Analytics-DAX-4472C4)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Data%20Preparation-Power%20Query-217346)](https://learn.microsoft.com/en-us/power-query/)
[![Portfolio](https://img.shields.io/badge/Project-Portfolio-138A8A)](#project-overview)

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Objectives](#business-objectives)
- [Executive Dashboard](#dashboard-showcase)
- [Key Performance Indicators](#key-performance-indicators)
- [Analytical Approach](#analytical-approach)
- [Data Model](#data-model)
- [Technology Stack](#technology-stack)
- [Business Value](#business-value)
- [Dataset and Assumptions](#dataset-and-assumptions)
- [Limitations and Future Enhancements](#limitations-and-future-enhancements)
- [Repository Structure](#repository-structure)
- [How to Explore the Project](#how-to-explore-the-project)
- [About the Author](#about-the-author)

---

## Project Overview

Retail businesses must balance product availability, inventory investment, supplier relationships, and profitability. Poor visibility into stock levels and purchasing requirements can lead to stockouts, excessive working capital, and missed sales opportunities.

This project uses **Power BI, DAX, Power Query, and dimensional modeling** to build an interactive analytical solution for evaluating inventory health and supporting operational decisions.

The report combines executive-level KPIs with detailed product, category, supplier, profitability, and replenishment analysis. It also includes an interactive what-if simulator to explore how alternative assumptions affect estimated purchasing requirements and budgets.

**Project scope**
- **Dataset:** 1,000 records and 11 source fields.
- **Report:** 8 interactive analytical pages.
- **Business domains:** Inventory management, procurement, supply chain, and commercial performance.
- **Core capabilities:** KPI reporting, ABC/Pareto classification, profitability estimation, supplier exposure analysis, replenishment calculations, and scenario analysis.

## Business Objectives

The project addresses the following business questions:

1. Which products require replenishment based on their current stock and reorder points?
2. What is the financial value of current inventory?
3. Which products contribute most to inventory value under an ABC/Pareto classification?
4. What are the estimated sales, cost of goods sold, gross profit, and gross margin?
5. How is inventory value distributed across suppliers and product categories?
6. What purchasing quantities and estimated budget are implied by current replenishment rules?
7. How do alternative scenario assumptions change replenishment requirements?
8. How can product-level diagnostics support more informed inventory and purchasing decisions?

## Dashboard Showcase

The report is organized into eight pages, progressing from executive monitoring to detailed operational analysis.

### 01. Executive Overview

![Executive Overview](screenshots/01-executive-overview.png)

Provides a consolidated view of inventory value, commercial performance, gross margin, low-stock exposure, and replenishment indicators.

**Business focus:** Understand the overall position quickly and identify areas that may require management attention.

### 02. Inventory Intelligence & Reorder Risk

![Inventory Intelligence](screenshots/02-inventory-intelligence.png)

Analyzes inventory status against reorder thresholds to identify products requiring attention and quantify stock shortfalls.

**Business focus:** Prioritize inventory exceptions and assess replenishment needs.

### 03. ABC Classification & Pareto Analysis

![ABC Pareto Analysis](screenshots/03-abc-pareto-analysis.png)

Examines the distribution of inventory value across products and applies ABC classification to distinguish high-value items from the rest of the portfolio.

**Business focus:** Support differentiated inventory control and prioritization based on economic value.

### 04. Sales Performance & Profitability

![Sales and Profitability](screenshots/04-sales-profitability.png)

Evaluates estimated sales, cost of goods sold, gross profit, and gross margin using the available unit cost, retail price, and sales volume fields.

**Business focus:** Understand estimated product economics and compare commercial contribution.

### 05. Procurement Intelligence & Supplier Exposure

![Procurement and Supplier Exposure](screenshots/05-procurement-supplier-exposure.png)

Explores inventory and commercial measures by supplier to provide visibility into supplier-level exposure and portfolio distribution.

**Business focus:** Support supplier reviews and identify areas for further procurement analysis.

### 06. Replenishment Planning

![Replenishment Planning](screenshots/06-replenishment-planning.png)

Quantifies replenishment gaps and estimated purchasing requirements using stock levels, reorder points, and unit costs.

**Business focus:** Translate inventory exceptions into measurable purchasing requirements.

### 07. What-if Inventory & Procurement Simulator

![What-if Simulator](screenshots/07-what-if-simulator.png)

Allows users to test alternative assumptions and evaluate their impact on estimated replenishment quantities and purchasing budgets.

**Business focus:** Compare scenarios and understand the financial implications of changing planning assumptions.

### 08. Product Deep Dive & SKU Diagnostics

![Product Deep Dive](screenshots/08-product-deep-dive.png)

Provides a detailed view of individual products, including inventory position, unit economics, and reorder-related indicators.

**Business focus:** Investigate specific SKUs and support product-level operational decisions.

---

## Key Performance Indicators

The following figures represent the report's current unfiltered baseline. Monetary values retain the source report's `$` formatting; the source currency has not been independently established as USD.

| KPI | Baseline result | Business interpretation |
|---|---:|---|
| Units Sold | 137,040 | Total reported sales volume |
| Estimated Sales | $3,831,549 | Sales volume multiplied by retail price |
| Estimated Gross Profit | $1,631,171 | Estimated sales less estimated cost of goods sold |
| Estimated Gross Margin | 42.57% | Estimated gross profit as a share of estimated sales |
| Inventory Value | $1,965,608 | Closing stock valued at unit cost |
| Products Below Reorder Point | 61 | Products or records identified below their reorder threshold |
| Replenishment Gap | 2,509 units | Aggregate positive stock shortfall against reorder points |
| Estimated Replenishment Budget | $39,593.35 | Estimated cost associated with replenishment quantities |
| Low-stock Inventory Value | $79,570 | Inventory value associated with records classified as low stock |
| Suppliers Represented | 10 | Number of suppliers in the dataset |

These indicators provide a starting point for understanding inventory exposure, purchasing needs, and estimated commercial performance. They should be interpreted in the context of the available dataset and calculation assumptions.

## Analytical Approach

### 1. Data Preparation

Power Query is used to prepare and structure the source data for reporting. The workflow emphasizes consistent field types, usable dimensions, and a reliable analytical foundation.

### 2. Dimensional Modeling

The report uses a fact-and-dimension modeling approach to organize inventory measures and descriptive attributes.

### 3. DAX Measures and Business Logic

DAX is used to calculate operational and commercial indicators, including inventory value, replenishment gaps, estimated sales, estimated gross profit, and gross margin.

### 4. ABC/Pareto Analysis

Products are classified according to their cumulative contribution to inventory value, using 80% and 95% thresholds to distinguish Classes A, B, and C.

### 5. Supplier and Procurement Analysis

Inventory and commercial indicators are analyzed across supplier and product dimensions to improve visibility into the structure of the portfolio.

### 6. What-if Scenario Analysis

Interactive parameters allow users to explore how changes in assumptions influence estimated replenishment quantities and purchasing budgets.

### 7. Decision-Oriented Reporting

The eight-page report combines executive KPIs, comparisons, detailed diagnostics, and scenario controls to connect quantitative analysis with practical business questions.

## Data Model

The analytical model is organized around a central inventory fact table and supporting dimensions.

| Table | Purpose |
|---|---|
| `FactInventory` | Inventory quantities, sales volume, unit cost, retail price, and reorder-related measures |
| `DimProduct` | Product identifiers and descriptive attributes |
| `DimCategory` | Product category attributes |
| `DimSupplier` | Supplier identifiers and descriptive attributes |

The dimensional structure is intended to support reusable measures, consistent filtering, and analysis across products, categories, and suppliers.

See [`docs/DATA_MODEL.md`](docs/DATA_MODEL.md) for the model documentation.

## Key KPI Definitions

### Inventory Value

Measures closing inventory at unit cost.

`Inventory Value = Closing Stock × Unit Cost`

The result represents the estimated cost value of current stock under the model's aggregation logic.

### Replenishment Gap

Calculates the positive difference between the reorder point and closing stock for each applicable record.

`Replenishment Gap = MAX(Reorder Point − Closing Stock, 0)`

The aggregate indicates the number of units required to bring below-threshold records up to their reorder points under the current logic. It is not an optimized purchase order.

### Estimated Sales

`Estimated Sales = Units Sold × Retail Price`

Estimates sales value using the unit retail price and reported units sold.

### Estimated Cost of Goods Sold

`Estimated COGS = Units Sold × Unit Cost`

Estimates the cost associated with reported sales volume.

### Estimated Gross Profit

`Estimated Gross Profit = Estimated Sales − Estimated COGS`

### Estimated Gross Margin

`Estimated Gross Margin % = Estimated Gross Profit ÷ Estimated Sales`

### Low-stock Inventory Value

Measures the inventory value associated with records classified as `Low Stock`. It is an indicator of stock-related exposure, not a measure of overstock or obsolescence.

### ABC Classification

Classifies products based on cumulative inventory value contribution:

- **Class A:** Products contributing to the first 80% of cumulative value.
- **Class B:** Products contributing from 80% to 95%.
- **Class C:** Products contributing to the remaining share.

The classification is intended to support differentiated inventory-management priorities.

See [`docs/KPI_DICTIONARY.md`](docs/KPI_DICTIONARY.md) for additional KPI definitions.

## Technology Stack

| Technology | Application |
|---|---|
| Power BI Desktop | Interactive report development and visualization |
| DAX | Business measures, calculations, classification logic, and scenario analysis |
| Power Query | Data preparation and transformation |
| Dimensional Modeling | Fact-and-dimension organization for analytical reporting |
| Excel | Source-data inspection and supporting analysis |
| GitHub | Project documentation and portfolio presentation |

## Business Value

This project demonstrates how data analysis can support business operations beyond presenting descriptive metrics.

The report provides a structured way to:

- Identify inventory records that fall below reorder thresholds.
- Quantify estimated stock shortfalls and purchasing requirements.
- Prioritize products by inventory-value contribution.
- Examine estimated product economics and gross margin.
- Explore supplier-level inventory exposure.
- Compare purchasing scenarios before making operational decisions.
- Communicate analytical assumptions and limitations clearly.

The intended outcome is a more transparent, measurable basis for inventory and procurement discussions.

## Dataset and Assumptions

The source dataset contains 1,000 records and 11 fields:

`Product ID`, `Product Name`, `Category`, `Supplier Name`, `Unit Cost`, `Retail Price`, `Opening Stock`, `Units Sold`, `Closing Stock`, `Reorder Point`, and `Stock Status`.

The calculations depend on the source values, data grain, relationships, and defined DAX logic.

Important assumptions include:

- Monetary calculations use the unit cost and retail price provided in the dataset.
- Estimated sales and profitability do not necessarily represent audited accounting results.
- Replenishment calculations use reorder points and closing stock under the current model logic.
- ABC classification uses inventory value at unit cost.
- Scenario results represent the selected assumptions rather than guaranteed outcomes.

## Limitations and Future Enhancements

The current project focuses on snapshot-based inventory and commercial diagnostics. Its analytical scope should not be confused with a full enterprise planning or forecasting solution.

Potential future enhancements include:

- Historical inventory and sales data for trend analysis.
- Demand forecasting and forecast-accuracy measurement.
- Supplier lead times and purchase-order history.
- Minimum order quantities and supplier pack-size constraints.
- Safety-stock policies and service-level targets.
- Supplier delivery, quality, and OTIF performance metrics.
- More advanced replenishment optimization and working-capital analysis.

These enhancements would require additional source data and business rules.

## Repository Structure

```text
retail-inventory-supply-chain-analytics/
├── README.md
├── .gitignore
├── powerbi/
│   └── Retail_Inventory_Supply_Chain_Analytics.pbix
├── screenshots/
│   ├── 01-executive-overview.png
│   ├── 02-inventory-intelligence.png
│   ├── 03-abc-pareto-analysis.png
│   ├── 04-sales-profitability.png
│   ├── 05-procurement-supplier-exposure.png
│   ├── 06-replenishment-planning.png
│   ├── 07-what-if-simulator.png
│   └── 08-product-deep-dive.png
├── data/
│   └── README.md
└── docs/
    ├── DATA_MODEL.md
    ├── KPI_DICTIONARY.md
    └── VALIDATION_CHECKLIST.md
```

The Power BI file and screenshots should be included only when they are available for sharing. Source data should be published only when redistribution is permitted.

## How to Explore the Project

1. Review the eight dashboard screenshots in the [Dashboard Showcase](#dashboard-showcase).
2. Explore the KPI definitions and analytical methodology.
3. Review the data model and supporting documentation in the `docs/` folder.
4. Open the `.pbix` file in Power BI Desktop, if included, to interact with the report and scenario controls.
5. Consider the stated assumptions and limitations when interpreting the results.

## About the Author

I am a Computer Science Engineer and entrepreneur with hands-on B2B experience in business operations, procurement, supplier negotiation, pricing, cost analysis, quotations, inventory management, logistics, and operational decision-making.

My professional background combines practical business experience with ongoing development in business intelligence and data analytics, using Power BI, DAX, Power Query, SQL, and Excel to structure business questions and translate data into decision-oriented insights.

This project reflects my approach to analytical problem-solving: understand the business context, define meaningful indicators, organize data for analysis, build an interactive reporting solution, and communicate the assumptions behind the results.

## Disclaimer

This is an independent portfolio project for demonstration and professional development. Report outputs depend on the available dataset, model structure, calculation logic, and stated assumptions. Estimated financial indicators and replenishment quantities should not be treated as audited financial results or as authorization to place purchase orders.

