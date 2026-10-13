# KPI dictionary

Definitions below reflect the current report intent. Validate final DAX and model behavior before treating each definition as production-approved.

| KPI | Definition / interpretation | Caveat |
|---|---|---|
| Inventory Value | Closing Stock × Unit Cost, summed over relevant fact rows | Reconcile with fact grain and relationships |
| Products Below ROP | Count of products/records below reorder point | Confirm unique-product logic and status rules |
| Replenishment Gap | Sum of `MAX(Reorder Point - Closing Stock, 0)` across fact rows | Not an optimized order quantity |
| Low-stock Inventory Value | Inventory Value filtered to `Stock Status = "Low Stock"` | Does not measure overstock or obsolescence |
| Estimated Sales | Units Sold × Retail Price | Not audited revenue |
| Estimated COGS | Units Sold × Unit Cost | May omit discounts, returns, freight, taxes, and adjustments |
| Estimated Gross Profit | Estimated Sales − Estimated COGS | Estimate from available fields |
| Estimated Gross Margin % | Estimated Gross Profit ÷ Estimated Sales | Validate blank/zero denominator behavior |
| Estimated Replenishment Budget | Replenishment quantity × Unit Cost under current logic | Not an approved purchase order |
| ABC Class | Cumulative inventory value at cost; intended thresholds 80% and 95% | Validate global denominator, ties, blanks, and non-positive values |
