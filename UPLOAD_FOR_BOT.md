# Bot upload instructions

Push **the contents of this folder** as the GitHub repository root.

```
git init
git add .
git commit -m "CellMo two-track quotation system V0.4"
git branch -M main
git remote add origin <REPO_URL>
git push -u origin main
```

Must exist at repo root after push:

- `index.html`
- `jszip.min.js`
- `README.md`

Enable GitHub Pages on `main` / root so `index.html` is the site.

Do not wrap files in an extra parent folder such as `cellmo-quote-system/cellmo-quote-system/`.
