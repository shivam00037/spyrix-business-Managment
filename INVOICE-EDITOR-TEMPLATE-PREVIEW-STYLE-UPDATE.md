# SPYRIX Invoice Editor — Template Preview Style Update

## What changed

- Reorganised the invoice editor into a Template Preview-inspired three-panel workflow: template picker and invoice details on the left, a live A4 invoice canvas in the middle, and design tools on the right.
- Added a searchable, category-filtered quick template gallery and a link to all available templates.
- Split design tools into five inspector tabs: Colors, Fonts, Assets, Text, and Layout.
- Grouped uploaded assets together: business logo, payment QR, authorised signature, and invoice background artwork. Each supports preview, replace/remove, and relevant sizing or placement settings.
- Kept editable business/customer details, invoice metadata, line items, custom fields, notes, terms, and payment instructions in the invoice workflow.
- Added detailed editable printed copy and label controls for the invoice heading, dates, parties, item table, totals, payment details, and footer.
- Added click-to-edit behavior on the live invoice preview. Clicking a document section opens its corresponding inspector tab and scrolls to related detail fields. The selected preview block remains visibly outlined.
- Improved asset upload cards and hover states to feel more like an interactive design studio.

## Persistence

- The existing invoice design local-storage persistence and backend allowlists continue to include the logo, QR, signature, text labels, paper finish, watermark, and background artwork settings.
- Invoice business/customer data and item editing remain connected to the existing invoice save workflow.

## Validation performed

- TypeScript transpile parsing passed for the invoice editor, invoice design module, template preview page, and the two affected server route files.
- `node --check` passed for both server route files.
- CSS brace-balance check passed.
- Full Vite production build was not run because this source extraction does not include installed frontend dependencies.
