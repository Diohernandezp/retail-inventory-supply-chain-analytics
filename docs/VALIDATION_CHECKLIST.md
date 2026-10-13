# Validation checklist

Mark an item complete only after verifying it in Power BI.

## Data and model
- [ ] Confirm source-data publication rights and remove confidential information.
- [ ] Confirm the grain of `FactInventory`.
- [ ] Investigate repeated identifiers such as `PRD-1004` and `PRD-1006`.
- [ ] Verify dimension keys, relationship cardinality, and filter behavior.
- [ ] Reconcile row counts and key totals before and after relationships are applied.

## KPI validation
- [ ] Reconcile Inventory Value to a product-level calculation.
- [ ] Verify Products Below ROP counts products, not unintended duplicate rows.
- [ ] Reconcile Replenishment Gap to positive reorder-point deficits.
- [ ] Verify Low-stock Inventory Value filters the intended status.
- [ ] Reconcile Estimated Sales, COGS, Gross Profit, and Gross Margin.
- [ ] Validate ABC denominator, cumulative order, ties, and class totals.
- [ ] Clarify supplier product-count logic; investigate displayed total of 80.
- [ ] Verify scenario percentage formatting (100%, not 10000%).
- [ ] Reconcile estimated replenishment budget to the product-level table.

## Report quality
- [ ] Test slicers and cross-filtering on all pages.
- [ ] Ensure KPI titles match displayed values.
- [ ] Use “estimated” for non-audited financial metrics.
- [ ] Avoid unsupported claims about forecasting, lead times, OTIF, EOQ, or historical trends.
- [ ] Capture all eight screenshots with the exact filenames in `screenshots/README.md`.
- [ ] Refresh and reopen the final PBIX before committing it.
