# Data quality and reconciliation

The checks read the original CSVs and used decimal arithmetic for BRL amounts. Counts refer to records before any report filters.

| Check | Result |
|---|---|
| Key uniqueness | Orders, customers and products each had a nonblank unique primary key. All 112,650 order and item sequence pairs were unique. |
| Join coverage | 775 orders had no item lines. All item rows matched an order and product, and all orders matched a customer. |
| Multiple lines | 9,803 orders had more than one item line. |
| Date completeness | Purchase and estimated delivery dates were populated. Approval, carrier handoff and customer delivery timestamps were missing on 160, 1,783 and 2,965 orders respectively. |
| Status and date consistency | Eight of the 96,478 orders marked delivered lacked a customer delivery timestamp. They remain in status-based delivered counts. |
| Product category completeness | 610 products had a blank source category. Two populated categories lacked a translation and covered 13 products. |
| Translation join | All 71 Portuguese lookup keys were unique and nonblank. A source-level left join preserves 32,951 products. The exact saved Power Query output was unavailable for inspection. |

The untranslated keys are `portateis_cozinha_e_preparadores_de_alimentos` (10 products) and `pc_gamer` (3). Preserve missing dates and categories as missing at the source. The left join retains products even when translation is unavailable. The project notes describe adding `category_display_name` for reporting, and the PBIX visual definitions reference it.

| Reconciliation | Verified value |
|---|---:|
| Total orders | 99,441 |
| Order-item records | 112,650 |
| Orders with items | 98,666 |
| Orders without items | 775 |
| Delivered orders | 96,478 |
| All item revenue | R$13,591,643.70 |
| All freight charges | R$2,251,909.54 |
| Delivered item revenue | R$13,221,498.11 |
| Delivered average order value | R$137.04 |

The Executive Overview screenshot has Year and Category set to **All**. Its four cards agree with the CSV checks, including the abbreviated R$13.22M display.

