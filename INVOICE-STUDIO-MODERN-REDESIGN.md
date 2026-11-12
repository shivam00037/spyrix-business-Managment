# SPYRIX Invoice Studio — Modern Card Redesign

## Updated
- Reworked the invoice studio into a clearer three-panel workspace with a premium dark studio banner, separated card sections, larger form controls, and a more visible A4 preview stage.
- Improved item cards, upload cards, template/style cards, action buttons, responsive breakpoints, and neon-theme accents.
- Added a dedicated **Signature & approval** card to the invoice editor.
- Added signature image upload (PNG/JPG/WEBP), replace/remove controls, signatory name, designation, visibility toggle, and adjustable signature width.
- Added signature to the live invoice preview and print/PDF output.
- Extended shared invoice design defaults and server allowlists so signature metadata survives invoice creation and template-design saving.

## Run locally
From the project root:

```bash
npm install
npm run dev
```

## Notes
- Signature image uploads use the same image validation and 900 KB per-image limit as the existing logo and QR upload controls.
- The full Vite production build was not run in this environment because the extracted client dependency folder does not contain Vite. Install dependencies locally before building.
