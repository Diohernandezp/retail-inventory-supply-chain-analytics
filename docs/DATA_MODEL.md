# Data model

## Intended analytical structure

| Table | Intended role | Validation needed |
|---|---|---|
| `FactInventory` | Numeric inventory, sales, cost, price, and reorder attributes | Confirm row grain and repeated product IDs |
| `DimProduct` | Product-level descriptive attributes and product key | Confirm uniqueness of the dimension key |
| `DimCategory` | Category attributes | Confirm one row per category key |
| `DimSupplier` | Supplier attributes | Confirm one row per supplier key |

Before documenting cardinalities as final:
- verify each dimension key is unique;
- verify each fact row joins to intended dimension records;
- decide how repeated product IDs should be represented;
- test totals before and after adding product, category, and supplier attributes to visuals;
- document the intended grain and relationship direction.

Do not describe the model as fully validated until these checks are complete in the PBIX.
