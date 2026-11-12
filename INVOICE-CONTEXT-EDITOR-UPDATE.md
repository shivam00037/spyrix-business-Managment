# SPYRIX Invoice Context Editor & Theme Update

## What changed

- The Create Invoice flow starts with template selection. Choosing a template opens the canvas editor and hides the template gallery; the gallery can be reopened with **Change template**.
- In the invoice editor, the invoice canvas is on the left and contextual tools are on the right. Selecting text opens text styling controls (bold, italic, underline, size, colour, font family and alignment); selecting images opens upload, visibility, resize and placement controls; selecting the page opens page colour, typography, frame, header/table style and paper options.
- Added a dropdown for PDF, PNG and JPG export from the editor. PDF uses the browser print dialog; PNG/JPG use the invoice canvas renderer.
- Image upload and drag/drop controls remain available for the business logo, payment QR, signature and additional canvas images.
- Responsive editor styles stack the invoice canvas and inspector on mobile and adapt template selection and export menus for narrow screens.
- Workspace theme palettes are retained, with monochrome (black and white) as the default. Other themes use the shared accent tokens across the workspace and editor controls; the invoice template's own brand accent can still be configured separately.
- The existing XENMARK invoice structure is preserved.

## Run locally

From the project root (the folder containing `package.json`):

```powershell
npm install
npm run dev
```

The root `dev` script launches the frontend and backend without depending on the `concurrently` package. Configure `server/.env` for MongoDB and JWT as described in `BACKEND-SETUP.md`. Google sign-in is not needed for the current email/password-only flow.

## Checks performed

- Parsed JSX/JavaScript source with Babel's parser.
- Checked brace balance in changed stylesheets.
- Validated the generated ZIP archive.

A full Vite production build was not run in this environment because the available Rollup binary was platform-specific. Install dependencies on Windows with `npm install` before testing in the browser.
