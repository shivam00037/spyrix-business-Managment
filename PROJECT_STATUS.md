# SPYRIX INVOICE — project status

## Current update
- Dashboard carousel redesigned with six distinct slide palettes, a static document visual, workflow steps, navigation dots/arrows and alternating directional slide transitions.
- Dashboard metrics display active customer count, completed payment collections, outstanding balances and paid invoices using real records.
- Global search is tinted to the active red/burgundy/yellow/purple theme and receives an accent focus state.
- Added Burgundy · White · Black as a fourth selectable theme in the top-bar picker and Account Settings.
- SPYRIX shared logo SVG now displays the wordmark `SPYRIX` only.
- Intro HTML source is colocated in `client/src/pages/Intro/IntroDocument.html` beside its JSX host and CSS.
- User-facing pages are grouped under `client/src/pages/<PageName>/`; page components, local CSS and page-specific helpers remain together.
- Added broad mobile layout safeguards for search, module headings, forms, tables, templates and dashboard.

## Verification completed
- 36 frontend JS/JSX files parsed with the installed TypeScript parser: no syntax errors.
- All relative frontend imports resolved.
- 18 backend JavaScript files passed `node --check`.
- Intro inline JavaScript passed `node --check`.
- `styles.css` and `DashboardPage.css` parsed with tinycss2 without top-level CSS errors.
- A complete Vite production build could not be run because `npm install --prefix client` timed out in this environment.

## Before production
Run `npm install`, `npm run build`, and then exercise the app in a browser with a configured MongoDB URI. Verify mobile widths, authentication, demo persistence, invoice issuance, payment allocation, exports and all page actions.

## 2026-11-08 workflow UI refresh

- Dashboard carousel auto-advances every 3 seconds. The banner artwork is static; only a short slide/fade transition runs when the slide changes. Manual arrow and dot controls remain available.
- The global search field is tinted with the selected red/burgundy/yellow/purple theme colours.
- Sidebar navigation uses `Create Invoice`; Quotations, Recurring Invoices and Business Settings are not displayed in the sidebar. Their legacy routes/components remain in the source for compatibility but are not primary navigation entries.
- Main module screens include an 11-action workflow hub with working create, search, filter, refresh, navigation and CSV/JSON export shortcuts where relevant.
- Reports exports are generated from loaded workspace records. Empty reports return a useful empty-state message instead of a fake file.
- The Templates area uses the selection → preview or separate customisation studio flow.
- Static validation is required before delivery; a full install/build and interactive browser test must still be run on the developer machine.

## 2026-11-08 burgundy theme and dashboard polish

- Added Burgundy · White · Black as a fourth selectable theme and exposed it in both theme selectors.
- Added a compact SPYRIX S mark to the Grow Your Business sidebar panel.
- Dashboard carousel continues to rotate every 3 seconds; content now alternates left/right entrances with a short directional slide/fade transition.
- Each dashboard slide has an individual accent palette (crimson, teal, blue, amber, plum or cyan) on a dark premium base, while primary buttons and KPI cards use the selected workspace theme.
- Refined KPI card hierarchy, accent strips, icon tiles and supporting labels.
- Verified with TypeScript JSX parsing and PostCSS parsing; full Vite build and interactive browser test still need to be run locally.


## Invoice editor update (2026-11-09)
- Added a dedicated `/app/invoices/new` route and live invoice composer.
- Left-side controls edit business branding, customer snapshot, invoice dates/references, item descriptions/quantity/rate/discount/tax, notes, terms, footer, printed labels, template, brand colour, font, paper size and orientation.
- Right-side invoice preview updates immediately; browser print supports Save as PDF.
- Invoice drafts and issued invoices use the existing API/DataContext. Server-side invoice design allowlist now persists the additional label/layout properties, and customer snapshot overrides are preserved per invoice without changing the customer master record.
- Validation performed: all client JS/JSX files parsed, backend route passed `node --check`, CSS braces balanced. Full Vite bundle build was not run because Vite/Rollup dependencies are not installed in this extraction environment.


## 2026-11-12 intro-first and Google OAuth setup fix

- Root route `/` and `/intro` now render the existing Intro page instead of immediately redirecting to Login or Dashboard.
- Intro **Get Started**, **Login**, and footer workspace CTAs open the Login page; successful email/password or Google authentication continues to `/app/dashboard`. New users can choose Create Account on the login screen.
- Authentication brand link now uses React Router navigation back to the Intro page.
- Expanded Google OAuth setup guidance: create `client/.env` and `server/.env`, use the same real Web client ID in both, allow the exact dev origin, and restart the app after editing environment values.
- Validation: 47 frontend JS/JSX files parsed successfully; Intro inline JavaScript syntax and flow assertions passed. Vite production build remains blocked in this environment by the absent optional `@rollup/rollup-linux-x64-gnu` package.
