# Metrics and DAX

The PBIX visual definitions confirm measure references and the CSVs independently support the values below. The embedded model expressions were unavailable for inspection. Definitions describe the business logic, and the DAX functions describe concepts relevant to implementing or reviewing it.

| Metric | Business meaning |
|---|---|
| Total Orders | Distinct orders in scope, including orders without item lines |
| Orders With Items / Without Items | Order IDs with or without an item match |
| Delivered Orders | Distinct orders whose recorded status is delivered |
| Item Revenue / Freight Charges | Separate sums of item price and item freight across statuses |
| Delivered Item Revenue | Item price summed for delivered orders, excluding freight |
| Average Order Value | Delivered item value divided by distinct delivered orders |
| Non-Delivered Items Revenue / Non-Delivered Value % | Item value associated with other statuses, and its share of all item value. The source-level difference is R$370,145.59, or 2.72%. |
| Category contribution | Category's share of delivered item value. The exact denominator scope under slicers needs model verification. |
| Previous Month Delivered Revenue | Delivered item value in the previous purchase month |
| MoM Revenue Change / MoM Growth % | Current month minus previous month, expressed as an amount or relative to the previous month |

All monetary measures use BRL. The delivered metric is a status-based sum of item prices.

- `DISTINCTCOUNT` counts order IDs once even when multiple lines are in scope.
- `CALCULATE` evaluates an expression under modified filter context. `KEEPFILTERS` can intersect a delivered-status condition with existing filters on the same column.
- `DIVIDE` handles zero or blank denominators and supports an explicit alternate result where appropriate.
- `REMOVEFILTERS` can clear a category filter for a contribution denominator while retaining other filters, depending on its scope.
- Date-intelligence functions such as `DATEADD` can shift date context to a prior month when used with a suitable date table.

