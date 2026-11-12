# SPYRIX INVOICE — Monochrome UI Update

## What's changed

- **Black & White is now the default visual theme** across the intro page, login/register screens, sidebar, topbar, dashboard and workspace pages.
- Added a **Black & White** option to the workspace theme picker. The existing Burgundy, Red, Yellow and Purple options remain available.
- Added a theme toggle to the intro and authentication screens; the selected theme is saved in `localStorage` and shared between screens.
- Updated the dashboard hero with a darker monochrome treatment, layered artwork, diagonal detail and higher-contrast content.
- Restyled the shared page banner, KPI cards, panels, forms, tables, buttons, status labels and navigation to follow the reference system.
- Updated the Customers page separately because it uses its own page layout. The primary sidebar now follows the supplied reference order, with secondary workflow routes accessible from a collapsed More workspace group.
- Reworked the Inventory, Payments, Reports, Calendar, Downloads, Notifications, Account Settings and Template Studio views to use the same monochrome visual system while retaining their existing page actions and data sources.

## Run locally

1. Extract the ZIP.
2. Open a terminal in the project root.
3. Run `npm install`.
4. Configure the server environment using `server/.env.example` (if present) and provide a reachable MongoDB connection string.
5. Run `npm run dev`.

The root `npm run dev` script starts the Express API and Vite client together. `npm run build` builds the client.

## Validation note

The edited source passes JavaScript/JSX parsing for all 45 client source files, CSS parsing for all 11 client stylesheets, and parsing of the intro page's inline script. A production Vite build could not be completed in this extracted environment because the local dependency folder is missing Rollup's Linux optional package `@rollup/rollup-linux-x64-gnu`. Reinstall dependencies in the target environment with `npm install` before building.

## Scope note

The UI update does not add new external billing, email, payment-gateway or notification providers. Existing API/data behavior and demo fallbacks remain as implemented in the supplied project.
