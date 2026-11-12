# SPYRIX INVOICE — Simple Page Editing Guide

## Where to edit a page
Open `client/src/pages/`. Each page has its own folder. For pages converted to single-file editing, edit the `*Page.jsx` file in that folder: page configuration and page-specific CSS are embedded in that same JSX file.

Examples:
- Dashboard: `Dashboard/DashboardPage.jsx` (dashboard has a larger dedicated layout; its styling remains in the Dashboard folder)
- Customers: `Customers/CustomersPage.jsx`
- Products: `Products/ProductsPage.jsx`
- Invoices: `Invoices/InvoicesPage.jsx`
- Payments: `Payments/PaymentsPage.jsx`
- Expenses: `Expenses/ExpensesPage.jsx`
- Quotations: `Quotations/QuotationsPage.jsx`
- Calendar: `Calendar/CalendarPage.jsx`
- Inventory: `Inventory/InventoryPage.jsx`
- Reports: `Reports/ReportsPage.jsx`
- Recurring invoices: `Recurring/RecurringPage.jsx`
- Downloads: `Downloads/DownloadsPage.jsx`
- Imports: `Imports/ImportsPage.jsx`
- Documents: `Documents/DocumentsPage.jsx`
- Tools: `Tools/ToolsPage.jsx`
- Help: `Help/HelpPage.jsx`
- Notifications: `Notifications/NotificationsPage.jsx`
- Business settings: `BusinessSettings/BusinessSettingsPage.jsx`
- Account settings: `AccountSettings/AccountSettingsPage.jsx`

## Important
The common data forms, API calls and reusable behavior are intentionally kept in `pages/shared/ModulePage/ModulePage.jsx` so that a fix to shared functionality applies consistently to all the related pages. You normally do not need to edit that file for a page-specific design change.

Dashboard, Intro, Login/Register and Templates have more complex custom layouts, so their supporting styles/components remain in their own page folders rather than being flattened automatically; this avoids breaking existing functionality.

To run: open `client` in a terminal, run `npm install`, then `npm run dev`.
