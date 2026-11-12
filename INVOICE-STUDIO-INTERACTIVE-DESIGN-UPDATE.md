# SPYRIX Invoice Studio — Interactive Design Update

## Included changes

- Added five invoice paper background choices, each using the same invoice layout preview: Snow White, Warm Ivory, Ice Blue, Soft Blush and Fresh Sage. Selecting a card updates the live invoice paper background without changing invoice content or accent colour.
- Added one-click layout moods: Signature, Bold Impact, Elegant, Creative and Compact.
- Added optional paper textures (plain, dots, grid and diagonal).
- Added editable document watermark text and opacity controls.
- Added live preview zoom controls and reset.
- Added a document readiness meter for business identity, customer details, invoice items and logo.
- Extended the server-side design allowlists and sanitizers so the new options persist for account template settings and saved invoice designs.

## Validation

- JavaScript/JSX source passed TypeScript transpile parsing.
- Server JavaScript files passed `node --check`.
- Invoice Studio stylesheet passed PostCSS parsing.
- Full Vite build could not be run because dependencies are not cached in this environment; `npm ci --offline` stopped at the first missing package tarball.

On Windows, extract the project, run `npm install`, then `npm run dev` from the project folder.
