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

## 中文摘要

這是工廠利潤中心（Quote A）與研發打樣（Quote B）的雙軌報價網頁。  
**`index.html` 與 `jszip.min.js` 必須放在同一層。** 用 GitHub Pages 開根目錄，或用 Chrome 直接開 `index.html`。

匯出前一定要填客戶、聯絡人、Email，否則欄位反紅、不會出檔。  
預覽窗常常不跳另存新檔，成功後看頁頂綠色「點這裡下載 Excel」。

Quote 單號：`C` + 國家碼 + 年 + 週 + 流水。有效日固定 +30。Quote A 自動拿掉 NRE。

---

Internal / CellMo use. Do not publish customer names or real BOM costs to a public repo unless intended.
