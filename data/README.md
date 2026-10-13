# Retail Inventory & Supply Chain Analytics

**Interactive Power BI portfolio project | Inventory health · ABC/Pareto · Estimated profitability · Supplier exposure · Replenishment scenarios**

> **Project type:** Independent portfolio case study  
> **Tools:** Power BI Desktop, DAX, Power Query, Excel  
> **Data scope:** 1,000 rows × 11 fields  
> **Report scope:** 8 pages  
> **Status:** Portfolio project. Model and KPI validation checks are documented below.

## Overview

This project explores how a retail business can use an inventory snapshot to assess stock risk, working-capital exposure, product-level economics, supplier concentration, and replenishment requirements.

The report moves from a portfolio-level overview to operational detail. It combines an interactive Power BI report, a dimensional data model, DAX calculations, and scenario analysis to support questions relevant to inventory, procurement, and operations teams.

The source is a snapshot dataset. Results should be interpreted as point-in-time diagnostics—not as a historical demand forecast, audited financial statement, or validated purchase-order recommendation.

## Business questions

- Which products are below their reorder point, and what is the aggregate unit shortfall?
- How is inventory value distributed across categories and suppliers?
- Which products account for the largest cumulative share of inventory value under an ABC/Pareto approach?
- What are the estimated sales, gross profit, and gross margin based on unit cost and retail price?
- How concentrated is inventory capital across suppliers?
- What purchase budget is implied by the current replenishment assumptions?
- How do scenario parameters affect estimated purchase units and budget?

## Dashboard pages

Click a screenshot link after adding the corresponding image to `screenshots/`.

| Page | Report section | Analytical purpose | Screenshot |
|---|---|---|---|
| 01 | Executive Overview | Summarize inventory value, estimated sales, gross margin, low-stock value, and key risk messages. | [View page 01](screenshots/01-executive-overview.png) |
| 02 | Inventory Intelligence & Reorder Risk | Identify products below reorder point and quantify the replenishment gap. | [View page 02](screenshots/02-inventory-intelligence.png) |
| 03 | ABC Classification & Pareto Analysis | Examine inventory-value concentration and classify products by cumulative value contribution. | [View page 03](screenshots/03-abc-pareto-analysis.png) |
| 04 | Sales Performance & Profitability | Compare estimated sales, estimated costs, gross profit, and gross margin. | [View page 04](screenshots/04-sales-profitability.png) |
| 05 | Procurement Intelligence & Supplier Exposure | Explore inventory-capital distribution and supplier-level commercial measures. | [View page 05](screenshots/05-procurement-supplier-exposure.png) |
| 06 | Replenishment Planning & Purchase Recommendations | Review estimated replenishment units, budget, and product-level shortfalls. | [View page 06](screenshots/06-replenishment-planning.png) |
| 07 | What-if Inventory & Procurement Simulator | Test scenario assumptions and inspect estimated purchase-budget changes. | [View page 07](screenshots/07-what-if-simulator.png) |
| 08 | Product Deep Dive & SKU Diagnostics | Inspect product attributes, unit economics, stock levels, and reorder thresholds. | [View page 08](screenshots/08-product-deep-dive.png) |

## Snapshot findings in the current report

These values are visible in the supplied unfiltered PDF export. They are dashboard outputs, not independently audited business facts. Revalidate after the model checks below before using them in interviews or professional materials.

| KPI | Current report output | Interpretation |
|---|---:|---|
| Units sold | 137,040 | Sum of units sold in the dataset |
| Estimated sales | $3,831,549 | Units sold × retail price under the current model |
| Estimated gross profit | $1,631,171 | Estimated sales less estimated COGS |
| Estimated gross margin | 42.57% | Estimated gross profit ÷ estimated sales |
| Inventory value | $1,965,608 | Closing stock valued at unit cost, subject to model validation |
| Products below reorder point | 61 | Products/records flagged below reorder point under current report logic |
| Replenishment gap | 2,509 units | Aggregate positive difference between reorder point and closing stock |
| Estimated replenishment budget | $39,593.35 | Estimated cost associated with replenishment quantities |
| Low-stock inventory value | $79,570 | Inventory value filtered to `Stock Status = "Low Stock"` |
| Supplier count | 10 | Supplier names represented in the report |

**Currency note:** The report formats monetary values with `$`, but the source schema does not establish a currency code. Do not identify the amounts as USD until the currency is confirmed.

## Methodology and KPI definitions

### Inventory value
Intended definition: `Closing Stock × Unit Cost`, aggregated over relevant fact rows. Confirm that the fact-table grain and relationships do not cause unintended duplication.

### Replenishment gap
For each fact row: `MAX(Reorder Point − Closing Stock, 0)`. The DAX iterates over `FactInventory` and sums positive deficits.

This measures the units needed to bring below-threshold records up to their reorder point under the current logic. It is **not** an optimized order quantity or an approved purchase order; lead times, open purchase orders, minimum order quantities, supplier pack sizes, and a separately modeled safety-stock policy are not included.

### Low-stock inventory value
The report filters `[Inventory Value]` to rows where `Stock Status = "Low Stock"`. This is the cost value associated with low-stock records; it does not measure overstock, obsolescence, or every form of working-capital risk.

### Estimated sales and profitability
- `Estimated Sales = Units Sold × Retail Price`
- `Estimated COGS = Units Sold × Unit Cost`
- `Estimated Gross Profit = Estimated Sales − Estimated COGS`
- `Estimated Gross Margin % = Estimated Gross Profit ÷ Estimated Sales`

These are estimates, not audited accounting results. Discounts, returns, taxes, freight, overhead, and other accounting adjustments may not be represented.

### ABC/Pareto classification
The report intends to classify products by cumulative inventory value at unit cost, using thresholds of 80% and 95% for Classes A and B, with the remainder in Class C. Validate the global denominator and reconcile class totals to total inventory value. Tied product values can affect boundary behavior.

### What-if analysis
The simulator exposes assumptions that affect estimated purchase units and budget. These are scenario outputs, not forecasts. Verify percentage formatting and test minimum, baseline, and maximum parameter settings before publishing final screenshots.

## Data model

The intended dimensional model contains:
- **FactInventory** — inventory, sales, cost, price, and reorder-related numeric fields.
- **DimProduct** — product identifiers and attributes.
- **DimCategory** — category attributes.
- **DimSupplier** — supplier attributes.

Confirm the fact-table grain, dimension-key uniqueness, relationship cardinality, and filter behavior before describing the model as fully validated.

### Source fields

The provided dataset is described as 1,000 rows and 11 fields: `Product ID`, `Product Name`, `Category`, `Supplier Name`, `Unit Cost`, `Retail Price`, `Opening Stock`, `Units Sold`, `Closing Stock`, `Reorder Point`, and `Stock Status`.

The schema does not include transaction dates, purchase-order history, lead times, MOQ, returns, or supplier-quality/OTIF fields.

## Validation notes before publication

1. **Product key and grain:** the report export shows repeated identifiers such as `PRD-1004` and `PRD-1006` with different values. Confirm whether these are valid separate records, variants, supplier-specific records, or duplicates. Do not assume `Product ID` is unique until resolved.
2. **ABC total and classes:** validate the global inventory-value denominator and reconcile Class A/B/C totals. Test tied values and blank/non-positive inventory values.
3. **Supplier product count:** the supplier scorecard shows a total product count of 80 while individual supplier rows show counts between 48 and 63. Confirm whether this counts distinct products across suppliers, fact rows, or another grain, then label it accordingly.
4. **Scenario formatting:** verify that purchase coverage displays as a percentage correctly (for example, 100%, not 10000%) and test all parameter endpoints.
5. **Risk wording:** “Low-stock inventory value” is more precise than “Capital at Risk” unless the latter is explicitly defined as stockout exposure.
6. **Purchase recommendations:** label units and budget as estimates based on the current snapshot and current DAX logic.

Only mark a check as complete after verifying it in Power BI.

## Scope and limitations

The report supports point-in-time inventory and commercial diagnostics. The current data does **not** support reliable claims about:
- historical sales or inventory trends over time;
- forecast accuracy or demand forecasting;
- days of inventory coverage or time-based turnover;
- economic order quantity (EOQ) optimization;
- supplier on-time delivery, quality, or OTIF performance;
- approved purchase orders or confirmed supplier lead times;
- audited revenue, profit, or cash-flow results.

These limitations distinguish measured outputs from assumptions and identify what additional data would be needed for a production-grade solution.

## Tools and techniques

- **Power BI Desktop** — report development and interactive analysis.
- **Power Query** — data preparation and transformation.
- **DAX** — measures, calculated logic, KPI definitions, and scenario calculations.
- **Dimensional modeling** — fact-and-dimension organization for analytical reporting.
- **Excel / source-data review** — dataset inspection and validation.

## Repository structure

```text
retail-inventory-supply-chain-analytics/
├── README.md
├── .gitignore
├── powerbi/
│   └── Retail_Inventory_Supply_Chain_Analytics.pbix  (add after validation)
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

Add the `.pbix` only if you are comfortable sharing the model and it contains no confidential data. Publish source data only if you have permission to redistribute it.

## How to explore the project

1. Open the eight screenshot links above to review each report page.
2. Read the KPI definitions and validation notes to understand what the measures do—and what they do not claim.
3. If the `.pbix` is published, open it in Power BI Desktop to interact with filters, drill-downs, and scenario controls.
4. Use the validation checklist to review what remains before operational deployment.

## About the author

I am a Computer Science Engineer and entrepreneur with practical B2B experience across operations, procurement, supplier negotiation, pricing, cost analysis, quotations, inventory, logistics, customer requirements, and operational decision-making. I am building on that business background with hands-on work in Power BI, DAX, Power Query, SQL, and analytical reporting.

This portfolio project demonstrates how I approach a business problem, define operational indicators, build an interactive report, and document assumptions and data limitations transparently.

## Disclaimer

This is an independent portfolio project for demonstration and learning purposes. Results depend on the supplied dataset, model design, DAX logic, and stated assumptions. They should not be used as audited financial information or as purchase authorization without further validation.
