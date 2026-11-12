# SPYRIX Invoice Designer — Reference UI and Canvas Editing Update

This update keeps the existing Xenmark invoice template and its print layout intact. Changes are in the editor workspace, mobile ordering, canvas editing helpers, and shared monochrome workspace styling.

## Invoice editor

- The editor uses a three-column desktop workspace: template gallery and quick tools, live invoice canvas, and Design / Elements / Fonts / Advanced inspector tabs.
- The template gallery now includes All, Business, Modern and Minimal filters and a working Browse All action.
- Click the invoice's editable wording and type directly on the document; changes are committed when the edit loses focus. Labels, customer and business details, dates, descriptions, quantities, rates, footer wording and other template text are editable in place. Calculated amounts remain derived from invoice line values.
- Use **Elements** for logo, payment QR, signature and additional artwork uploads. Images remain editable after upload.
- Drag a PNG/JPG/WEBP image file from your desktop onto the invoice to position it where dropped. Additional canvas images can be moved with their move handles, resized from Elements and removed. Drag the move handle on the logo, QR or signature to float the asset anywhere on the page; use **Dock** to restore its original template position.
- On phones and narrow tablets, the live canvas appears before the template gallery and inspector. Inspector tabs and form controls wrap within the viewport, and the invoice's item rows use the existing stacked mobile layout.

## Dashboard tabs

The existing MonochromeTheme stylesheet and page-specific components provide the black-and-white reference treatment for customers, inventory, payments, reports, calendar, downloads, account settings, notifications and invoice templates. This update retains those routes and their data workflows and keeps their responsive layout styles.

## Run

From the project root:

```powershell
npm install
npm run dev
```

`npm run dev` launches the API and Vite using `scripts/dev.js` and no longer depends on the missing `concurrently` executable. MongoDB and Google OAuth still require configuration in the local environment files for live account/data features.

## Validation

- JavaScript/JSX syntax parsing passed for all 68 frontend/backend/script source files.
- Modified CSS brace-balance checks passed.
- A production Vite build could not be run in this environment because npm could not download the required `@vitejs/plugin-react` tarball from the package registry. Run `npm install` and `npm run build` locally to validate the complete bundle on your machine.
