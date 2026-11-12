# SPYRIX INVOICE — Email Login Update

The app now follows this startup flow: **Intro page → Login/Create Account → Dashboard**. Opening `http://localhost:5173/` displays the intro landing page first. Its **Get Started** and **Login** buttons open the login screen; new users can choose **Create account** there. Successful authentication opens the protected dashboard.

Google sign-in is intentionally disabled for now. Use email/password registration and login; no Google Client ID is needed. Google sign-in can be added later.

---

# SPYRIX INVOICE — VS Code-ready MongoDB workspace

A React + Vite frontend, Express API and MongoDB/Mongoose data layer. The app opens on the public intro page, then login, then the dashboard after successful authentication. All business workspace pages require an authenticated account, with MongoDB-backed storage.

## First screen and user flow

1. Run the application and open `http://localhost:5173/` to view the intro page.
2. Click **Get Started** or **Login**, then sign in with an existing email/password account or select **Create account**.
3. After successful registration/login, the user enters `/app/dashboard`. Unauthenticated visits to workspace routes always return to login.
4. There is no guest/demo access; workspace data is loaded from the authenticated MongoDB API.

The app uses HashRouter (`/#/...`) so it works with Vite locally and does not depend on server-side route rewrites.

## Page folders

Every main page has its own React folder under `client/src/pages/`, containing its JSX, page CSS and `page.config.js` JavaScript configuration. See `client/src/pages/PAGE-STRUCTURE.md` for the full list. For example:

```text
client/
  src/pages/Auth/AuthPage.jsx # Login/register entry page
  src/
    pages/
      Auth/AuthPage.jsx
      Auth/AuthPage.css
      Dashboard/DashboardPage.jsx
      Dashboard/DashboardPage.css
      Invoices/InvoicesPage.jsx
      Invoices/InvoicesPage.css
      Invoices/invoiceDesign.js
      Templates/TemplatesPage.jsx
      Templates/TemplateStudio.jsx
      Templates/TemplateStudio.css
      Quotations/QuotationsPage.jsx
      Quotations/QuotationsPage.css
      Customers/CustomersPage.jsx
      Customers/CustomersPage.css
      Customers/components/CustomerPicker.jsx
      Products/ProductsPage.jsx
      Inventory/InventoryPage.jsx
      Payments/PaymentsPage.jsx
      Expenses/ExpensesPage.jsx
      Reports/ReportsPage.jsx
      Calendar/CalendarPage.jsx
      Recurring/RecurringPage.jsx
      Documents/DocumentsPage.jsx
      Notifications/NotificationsPage.jsx
      Downloads/DownloadsPage.jsx
      Backups/BackupsPage.jsx
      Imports/ImportsPage.jsx
      BusinessSettings/BusinessSettingsPage.jsx
      AccountSettings/AccountSettingsPage.jsx
      Help/HelpPage.jsx
      Tools/ToolsPage.jsx
      shared/ModulePage/ModulePage.jsx # Shared table/form/CRUD UI
```

Every main route is placed in its own folder with a dedicated page component, a page-scoped CSS file and a `page.config.js` file for page-specific JavaScript settings (Template Studio uses its own `TemplateStudio.css`). The page components pass an explicit module key to the shared CRUD engine; this keeps customer/invoice/payment validation consistent while letting you change a specific module's design and page settings without changing other tabs. The Dashboard, Intro, Authentication and Template Studio have standalone page implementations. Each page folder also has a short README describing where its code and data rules live.

## Recommended VS Code setup

1. Extract the ZIP.
2. Open the `spyrix-invoice-mongodb` folder in VS Code (`File → Open Folder`).
3. Open the VS Code terminal (`Terminal → New Terminal`).
4. Install dependencies once:

```powershell
npm install
```

The root postinstall installs packages for `client` and `server`. If needed, install separately:

```powershell
npm install --prefix client
npm install --prefix server
```

### Run full MongoDB application

Create `server/.env` from the example:

```powershell
Copy-Item server\.env.example server\.env
notepad server\.env
```

Set a valid MongoDB connection string and a long private JWT secret:

```env
MONGODB_URI=mongodb://127.0.0.1:27017/spyrix_invoice
JWT_SECRET=replace-with-a-long-random-secret-at-least-32-characters
JWT_EXPIRES_IN=7d
PORT=5000
CLIENT_ORIGIN=http://localhost:5173
NODE_ENV=development
```

Then run:

```powershell
npm run dev
```

Open `http://localhost:5173/`. Keep this terminal open. The API health endpoint is `http://localhost:5000/health`.

You can also double-click `Start-SPYRIX.bat`. In VS Code, press `Ctrl+Shift+P`, choose **Tasks: Run Task**, and select **SPYRIX: Start full app (MongoDB + UI)**.

### Run frontend/backend separately

```powershell
npm run dev:server
```

In a second terminal:

```powershell
npm run dev:client
```

If Vite port `5173` is busy, Vite is configured to select the next available port. The frontend uses `http://localhost:5000/api/v1` as its default API base; update `client/.env` only if your API is hosted elsewhere.

### Build

```powershell
npm run build
```

## Implemented workflows

- Login/register entry is required before the authenticated dashboard; no guest or demo mode is available.
- MongoDB account registration/login with JWT and one business workspace per registered account.
- Dashboard with six auto-rotating workflow banners (each has its own visual style, steps and navigation action), alternating left/right slide transitions, business metrics, collections and recent activity.
- Customer CRM with generated unique customer IDs (`CUS-...`), full contact/billing/GST fields, optional custom fields and a searchable picker by name, company, phone, GSTIN or customer ID.
- Invoice customer selection reuses saved data and saves a customer snapshot on the invoice so later edits to the customer master do not rewrite historical invoice details.
- Invoice editor supports product autofill, custom line items, per-line discounts, invoice custom fields, PO/reference fields and a shared server-side total calculation.
- Twenty invoice templates, including a Xenmark-maroon reference-inspired layout, plus custom accent colour, font, business identity, logo, payment QR, signature, UPI/payment instructions and footer settings. The print masthead keeps business identity visible beside an uploaded logo; selected fonts and accent colours carry through template-specific print styles. Authenticated workspaces save default design settings in MongoDB; each invoice stores its chosen design snapshot.
- Customer and product CRUD, invoice and quotation drafting/issuing, payment allocation and expense records.
- Inventory overview/manual stock adjustment, reports, billing calendar, local recurring reminders, notifications, CSV downloads, customer CSV import preview and authenticated JSON backup review.
- Black & White is the first-launch default theme across the login/register screens and workspace. Burgundy, red, yellow and purple themes remain selectable, along with the dark appearance option.

## Current MVP limitations

This is an extensible MVP, not a complete production accounting package. GST jurisdictional validation and inclusive-tax logic, immutable invoice revisions, inventory movement ledger and automatic stock deduction/reversal, a background recurring invoice scheduler, Razorpay, email/WhatsApp delivery, private attachment storage, full audit/role permissions, genuine server-generated DOCX/XLSX/PDF/PNG/JPG files, complete imports and live MongoDB restore still require implementation and testing. Invoice output currently uses a browser print view (users can choose Save as PDF); CSV export is implemented for available data lists. The 20 print layouts are distinct CSS compositions based on one invoice data model. Validate Indian tax handling with a qualified professional before real invoice issuance.

## Security

Never commit `server/.env`. Do not use the example JWT secret in production. Use HTTPS, a secure secret manager, MongoDB network access controls, tenant-isolation tests, audit trails and backup policies before deployment.


## VS Code page structure

Open the `spyrix-invoice-mongodb` folder in VS Code. All user-facing pages are grouped under `client/src/pages/`. Each page folder contains its own JSX component, page-scoped CSS and `page.config.js`; complex pages can have local `components/`, helper files and assets in the same folder. The first page is the login/register screen; workspace routes redirect unauthenticated visitors to login. The dashboard banner source remains in `client/src/pages/Dashboard/`. Its existing banner CSS and markup are preserved; KPI-only theme styling lives in `DashboardTheme.css`.

App-wide layout, authentication, data context, API helpers and design tokens live separately in `client/src/components/`, `client/src/context/`, `client/src/data/`, `client/src/api.js` and `client/src/styles.css`. Shared record primitives stay in `client/src/pages/shared/ModulePage/` so financial and CRUD behaviour remains consistent between tabs.

## Run in VS Code

1. Open this project folder in VS Code.
2. Run `npm install` in the integrated terminal. The root postinstall installs the client and server dependencies.
3. Copy `server/.env.example` to `server/.env` and set `MONGODB_URI` plus a long private `JWT_SECRET`.
4. Run `npm run dev` to start frontend and API together.
5. Authentication is required before any business workspace page can open.

The dashboard banner design, artwork, slide colours, controls and transitions are preserved. It rotates automatically every 3 seconds. Slides 1, 3 and 5 enter from the left; slides 2, 4 and 6 enter from the right. Only the slide change transitions; the banner artwork has no continuous decorative animation. Manual dots and arrow controls remain available, and the carousel honours reduced-motion settings.

## Workflow UI refresh (8 November 2026)

The latest UI pass includes a six-slide dashboard carousel with a 3-second interval and a short transition only (no continuous banner ornament animation), theme-filled global search, and an 11-action workflow shortcut hub on each main data module. The primary sidebar follows the supplied reference order: Dashboard, Invoices, Customers, Products, Inventory, Templates, Reports, Calendar, Brand Studio, AI Assistant, Settings and Profile. Secondary workflows remain accessible in the collapsed More workspace group.

The Templates route follows this flow: select a template, then choose Preview or open the separate Customise studio. Report shortcuts export CSV files from the records currently loaded in the active workspace. All workspace records are loaded from the authenticated MongoDB API.

Some operations remain development-scope limitations rather than production accounting features: recurring invoice background generation, validated GST compliance, integrated payment gateway processing, complete audit/stock movement ledgers, secure server-side bulk import/restore and the full DOCX/XLSX/PNG/JPG export engine need additional implementation and testing.

## SPYRIX AI Assistant

The workspace now includes an **AI Assistant** tab with text chat, browser-based speech input, and spoken replies. The chat endpoint is protected by the normal signed-in workspace authentication and keeps the OpenAI API key on the server.

To activate live AI answers:

1. Copy `server/.env.example` to `server/.env`.
2. Add your OpenAI API key to `OPENAI_API_KEY`. The example uses the cost-efficient `gpt-6-luna` model; change `OPENAI_MODEL` to another model available to your API project when you need a different capability/cost balance.
3. Keep `OPENAI_WEB_SEARCH_ENABLED=true` to let the assistant look up current information, or set it to `false` to disable web search.
4. Restart the backend. The browser client does not need an API key.

The ChatGPT Free/Plus/Pro subscription is separate from API usage. API access and billing must be enabled for the API key's OpenAI project. Voice capture uses the browser's Speech Recognition API where supported; spoken replies use the browser's Speech Synthesis API. These browser speech features do not require an additional speech API key.

AI API routes are protected and require a signed-in workspace account.


## Current invoice editor update

- Xenmark-inspired default invoice layout with in-place editable text and item values.
- Tap-to-upload business logo, payment QR, and signature images.
- Mobile-responsive invoice editing and site-level black-and-white default theme.
- Email/password authentication backed by Express, JWT, and MongoDB. Google sign-in is deferred until a later update.
- Setup steps and required environment variables are documented in [BACKEND-SETUP.md](BACKEND-SETUP.md).
#   s p y r i x - b u s i n e s s - M a n a g m e n t  
 