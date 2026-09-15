# Pricing logic (V0.4)

## Two tracks

| Track | When | Unit price | NRE on Excel |
|---|---|---|---|
| A Factory volume | Standard production order | `COGS × (1 + markup%)` | Removed |
| B Standard sample | In-spec sample, MOQ 20 pcs | `Quote A × multiplier` (default 1.5) | $0 |
| B Custom R&D | New recipe / tooling | `Quote A / (1 − RD%)` | One-time fee (default $1,500), rebateable on volume |

Markup 25% is **not** 25% gross margin. Gross margin = 20%.

## Yield

Materials, forming, sintering charge **started** area (`good / yield`).  
Machining and QC charge **good** area.

## Plant allocation

Annual rent + equipment + utilities are divided by the allocation m² field.  
If this SKU only uses part of the plant, lower the allocation m² or the implied utilization will overstate cost.

## Excel export

- Unit = pcs
- Prices under $10 keep 4 decimals (Fortescue-style)
- Valid until = quote date + 30 days
- Internal factory cost is never written to the customer sheet
- Quote A never writes the NRE line
- Quote number `C` + country + YY + ISO week + serial
