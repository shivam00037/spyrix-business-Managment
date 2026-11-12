# SPYRIX Invoice Workspace Update

## Invoice home
- A responsive banner introduces the Invoice Studio.
- Quick actions open Create Invoice, Browse Templates, Import Invoice Data, View Invoice Records, and Customers.
- Summary cards show total invoice count, issued invoice value, pending receivables, and customer count.
- Five featured invoice previews use the same shared `TemplateMiniPreview` component as the Template Studio. “View more templates” opens the full template gallery.
- The recent invoice column shows up to five saved invoices using each invoice's saved template, colour, font, logo scale, header, table, frame, QR and footer settings where those values are available.

## Invoice and template studio
- Create Invoice and Template Studio customization open the same three-column editor.
- Left: editable business, customer, contact, billing, tax, bank/UPI, logo, payment QR, dates, references, items, notes, terms and custom fields.
- Centre: live A4-style document preview.
- Right: template, accent and paper colours, typography, logo sizing and placement, frame/header/table styles, density, page size and orientation.
- Export uses the browser print dialog, where the user can save a PDF. Draft and issue actions use the existing invoice save flow.

## Themes
- Black & White remains the default. The global search field is black with white text in this theme.
- Neon Yellow & Black is available in the workspace theme picker, theme settings, login/register theme toggle and intro page theme toggle.
- Existing Burgundy, Red, Yellow and Purple theme options are retained.

## Run locally
From the project root, install the client and server dependencies using the package instructions in the README, configure the server environment from `server/.env.example`, then start the app using the existing project scripts. This package contains source only; `node_modules` is not included.
