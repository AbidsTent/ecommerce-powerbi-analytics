# Findings

These observations use all supplied data. Item lines were joined to orders, filtered to delivered status and summed by item price. State comes from the matched customer, category from the matched product, and month from the purchase timestamp.

| Question | Observation |
|---|---|
| Which customer state leads? | São Paulo (SP) leads at R$5,067,633.16, about 38.3% of delivered item revenue. Rio de Janeiro follows at R$1,759,651.13. |
| Which product category leads? | Health Beauty (`beleza_saude`) leads at R$1,233,131.72, ahead of Watches Gifts at R$1,166,176.98. |
| Which purchase month leads? | November 2017 leads at R$987,765.37. The screenshot presents it as approximately R$987.8K. |

State reflects customer location. Category rankings measure item value and do not account for margins, costs or units sold. The monthly trend groups by purchase month and uses the order's recorded delivered status. Coverage is partial at the edges of the historical window, so comparisons involving those periods require care. The report's text panel is static and describes the full dataset regardless of the slicer selection.

