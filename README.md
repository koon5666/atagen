# ATAgen — ATA Carnet Document Generator

Single-file web app for generating Thai ATA Carnet customs documents. No server, no install — open `index.html` in any browser.

## Documents

| Tab | Form | Purpose |
|-----|------|---------|
| Invoice | Custom invoice | Equipment list with values, quantities, serial numbers |
| ATA-1/2 | FM-ATA-01 + FM-ATA-02 | Submission documents for carnet issuance |
| ATA-7 | FM-ATA-08 + FM-ATA-09 | Return documents used when coming back to Thailand |

## Workflow

1. **Invoice tab** — fill in trip dates, destination, equipment preset
2. **ATA-1/2 tab** — enter carnet no., letter date, deposit, invoice no./date → Apply → Print
3. **ATA-7 tab** — return dates auto-filled from ATA-1/2; add return date and customs port → Apply → Print

## Features

- Equipment presets (Regular Kit 3 items / Kit + AR Omega 4 items)
- Carrier profile save/load
- Overlay text draggable to fix positioning
- Bookbank copy appended to ATA-7 print
- Print each tab separately — browser prints exact A4 pages

## Data flow

```
Invoice tab  ──►  ATA-1/2  ──►  ATA-7
(name, invNo,    (carnet no,    (pulls from ATA-1/2:
 invDate, dest)   date, deposit,  deposit, invNo, dest)
                  airport)
```

## Stack

Pure HTML/CSS/JS, no dependencies except PDF.js CDN for invoice photo rendering. All form backgrounds are embedded base64 JPEGs rendered from the original Thai Board of Trade PDF templates.
