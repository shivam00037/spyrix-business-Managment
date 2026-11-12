# Real Invoice Template Previews and Editor Fit Update

## What changed

- Replaced the grey/black placeholder template wireframes with a populated invoice preview component shared by the Invoice home, Template Gallery, and Create Invoice template selector.
- The preview displays realistic invoice content: brand block, invoice number/date, Bill To/Bill From, item descriptions and amounts, totals, payment QR styling, signature line and footer. It is preview artwork only, not saved as an invoice record.
- The Invoice home hero now shows a complete invoice sample rather than an empty line-wireframe.
- Added per-template style presets so choosing a template updates the live document's header style, table treatment, frame, density and accent to match the selected design family.
- Desktop Create Invoice editor now uses a 70/30 canvas-to-inspector split. The page scales to the full canvas width and keeps its page-like proportion while preserving content sizing.
- On mobile, the canvas can expand vertically rather than forcing the full invoice into a tiny fixed-height page. The editing tools stack beneath it.
- Export menu includes PDF, PNG and JPG and now uses a mobile-safe bottom-sheet menu with an outside-tap close layer.

## Run locally

From the extracted project root (the folder containing the root `package.json`):

```powershell
npm install
npm run dev
```

The root script starts both client and server. MongoDB/JWT configuration is still required for authenticated, database-backed use. Email/password login remains the only login UI; Google sign-in is left for a future update.

## Checks performed

- Parsed the client JavaScript/JSX sources with the installed TypeScript JSX parser.
- Checked CSS brace balance.
- Verified the template list and style-preset coverage.
- Validated the resulting ZIP archive.

A full Vite production build/browser interaction test was not available in this environment because the project's Vite dependency binary is not installed here. Run `npm install` on the target machine before launching.
