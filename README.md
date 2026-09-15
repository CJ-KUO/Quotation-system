# CellMo Two-Track Quotation System V0.4

Factory profit-center quoting (Quote A) and R&D sample quoting (Quote B).  
Browser-only. No server. Open `index.html` or enable GitHub Pages.

繁體中文說明見下方。

---

## Upload this folder as the GitHub repo root

Required at **repository root** (not inside a nested folder):

| File | Required | Purpose |
|---|---|---|
| `index.html` | yes | The quotation app (GitHub Pages entry) |
| `jszip.min.js` | yes | Excel export. Must sit next to `index.html` |
| `README.md` | yes | This file |
| `.gitignore` | yes | Ignore OS junk |

Do **not** upload `node_modules`, the Vite sandbox, or `.grok`.

### GitHub Pages

1. Create repo (example: `cellmo-quote-system`).
2. Push this folder as the root of `main`.
3. Settings → Pages → Source: Deploy from branch `main` / `/` (root).
4. Open `https://<org>.github.io/<repo>/`.

Local: keep `index.html` and `jszip.min.js` in the same folder, then open `index.html` in Chrome.

---

## What this version does

- **Quote A — factory volume.** COGS × (1 + factory markup %). No NRE on the customer Excel.
- **Quote B — samples.**
  - Standard stock sample: Quote A × 1.5, NRE = $0, MOQ 20 pcs (warning only).
  - Custom R&D: Quote A ÷ (1 − RD%), plus one-time NRE (default $1,500). NRE can be rebated on a later volume order.
- Money fields use `$000,000`.
- Dimensions: length × width × thickness, unit conversion, pcs ↔ m², yield.
- SKU dropdown fills standard size (still editable).
- Quote number: `C` + country + YY + ISO week + 2-digit serial  
  Example: `CU263701` = CellMo / Australia / 2026 / week 37 / #01.
- Valid until = today + 30 days.
- Export uses the CellMo Fortescue-style Excel (pcs pricing, logo). Internal costs are **not** written to the customer file.
- Tariff is optional, driven by incoterm.
- Empty required fields (customer / contact / email / product / size / pcs / lead time / HS) block export and turn red.
- Pricing **guide** is always visible. **Formulas** are collapsed until you click Show formulas.

---

## Default cost structure (editable in the page)

Variable USD / m² (placeholders until real BOM is keyed):

| Step | USD / m² | Basis |
|---|---:|---|
| Raw materials | 180 | started area |
| Forming | 40 | started area |
| Sintering | 45 | started area |
| Machining | 25 | good area |
| QC | 10 | good area |

Plant fixed (USD / year), allocated by annual m²:

- Rent + indirect labor `$258,065`
- Equipment `$129,032`
- Utilities `$64,516`
- Allocation base default `3,000 m²/year`
- Factory markup default `25%` = **20% gross margin** on selling price  
  (`GM = markup / (1 + markup)`)

R&D on custom Quote B: `15% of selling price` (adjustable).  
This page does **not** auto-check the NT$30M / ~USD 967k annual R&D budget.

---

## Formulas

```
Piece area (m²/pc)     = Length × Width   (converted to metres)
Good m²                = Piece area × pcs
Started m²             = Good m² / Yield
COGS / m²              = Variable (yield-adjusted) + plant fixed / allocation m²
Quote A                = COGS × (1 + markup %)
Quote B standard       = Quote A × 1.5
Quote B custom         = Quote A / (1 − RD%)   + NRE
COGS margin %          = COGS / Net Revenue
Factory GM %           = Markup % / (1 + Markup %)
Price / pc             = Price / m² × piece area
```

---

## Folder map

```
index.html                          # run this / GitHub Pages
jszip.min.js                        # required sibling of index.html
CellMo_TwoTrack_Quote_V0.4.html     # same file, named copy
README.md
.gitignore
docs/PRICING_LOGIC.md
samples/Quotation_Template_CellMo.xlsx
samples/Quotation_CU263801.xlsx     # generated example
samples/Quotation_SAMPLE.xlsx
analysis/breakeven_volume.xlsx
analysis/breakeven_volume_chart.png
archive/CellMo_Quote_System_v0.1_zh.html
```

---

## 中文摘要

這是工廠利潤中心（Quote A）與研發打樣（Quote B）的雙軌報價網頁。  
**`index.html` 與 `jszip.min.js` 必須放在同一層。** 用 GitHub Pages 開根目錄，或用 Chrome 直接開 `index.html`。

匯出前一定要填客戶、聯絡人、Email，否則欄位反紅、不會出檔。  
預覽窗常常不跳另存新檔，成功後看頁頂綠色「點這裡下載 Excel」。

Quote 單號：`C` + 國家碼 + 年 + 週 + 流水。有效日固定 +30。Quote A 自動拿掉 NRE。

---

Internal / CellMo use. Do not publish customer names or real BOM costs to a public repo unless intended.
