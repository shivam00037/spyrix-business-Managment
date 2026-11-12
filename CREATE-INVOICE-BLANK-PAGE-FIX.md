# SPYRIX INVOICE — Create Invoice Blank Page Fix

## What was fixed

The Create Invoice route was opening the invoice editor, but the editor crashed during its first render because `ListChecks` was used for the **Items & services** section without being imported from `lucide-react`.

The missing named import has been added in:

`client/src/pages/InvoiceCreator/InvoiceCreatorPage.jsx`

The route remains `/app/invoices/new`, and the shared invoice/template editor behavior is unchanged.

## Run the repaired project

1. Extract this ZIP into a new folder (or replace the previous project folder with this complete project).
2. Open a terminal in the project root.
3. Run `npm install`.
4. Run `npm run dev`.
5. Open SPYRIX, go to **Invoices**, then click **Create Invoice**.

If an older Vite server is already running, stop it with `Ctrl+C` before restarting it.
