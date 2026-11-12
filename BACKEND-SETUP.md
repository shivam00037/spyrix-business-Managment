# SPYRIX INVOICE — backend and mobile setup

## First-time user flow

Open `http://localhost:5173/` to see the public intro page first. The intro page’s **Get Started** and **Login** actions open the login screen; new users can choose **Create account** there. Only after successful email/password authentication does the app open the protected dashboard. Google sign-in is intentionally deferred and is not required. Visiting `/app/*` without a valid session redirects to login.

## What the backend stores

The default invoice designer is the Xenmark-style layout from the provided reference. On the invoice canvas, tap/click text to edit it in place; tap the logo, payment QR, and signature placeholders to upload images. The line-item table becomes compact editable cards on small phone screens. The rest of the workspace defaults to a monochrome black-and-white theme.

The Express API is in `server/`; MongoDB/Mongoose models are in `server/src/models/`. A signed-in user gets their own business workspace. Customer, product, invoice, payment, expense, quotation and business invoice-design data are scoped to that workspace. Email/password login uses bcrypt password hashes and JWT sessions. Google sign-in is disabled in the login UI for now and will be added later. Never publish secrets in the client bundle or commit `.env` files.

## 1. Install Node.js and MongoDB

Install a current LTS version of Node.js. You can use a local MongoDB Community Server or a MongoDB Atlas cluster. Create an empty database named `spyrix_invoice` (MongoDB creates it when the first records are written).

## 2. Configure the server

From the project root in PowerShell:

```powershell
Copy-Item server\.env.example server\.env
notepad server\.env
```

Set `MONGODB_URI` to your local or Atlas connection string and replace `JWT_SECRET` with a long random secret (at least 32 characters). Keep `PORT=5000` and add the exact frontend origin to `CLIENT_ORIGIN`.

## 3. Google sign-in (deferred)

Google sign-in is intentionally hidden for this version. You do not need a Google Client ID to register or sign in. Use the email/password form. When Google sign-in is added later, configure a real OAuth Web client ID in both environment files and update the login UI.

## 4. Install dependencies and start the app

From the project root:

```powershell
npm install
npm run dev
```

Keep the terminal open. The React/Vite app is usually at `http://localhost:5173`; the API is at `http://localhost:5000`. Check the API using `http://localhost:5000/health`. If Vite selects another port, add that port to `CLIENT_ORIGIN` in `server/.env` and restart the server.

You can also run the processes separately in two terminals:

```powershell
npm run dev:server
```

```powershell
npm run dev:client
```

## 5. How data saving works

For a registered email/password account, the frontend sends changes to `/api/v1/...` with the JWT. The API applies the authenticated user's business/workspace scope and stores records in MongoDB. The default invoice design is saved to the business settings; each invoice also stores a snapshot of its design and customer details. Guest/demo access is disabled. Workspace routes require an authenticated account.

The image/logo/QR/signature fields are stored as image data URLs within the business invoice-design object or invoice snapshot. This is suitable for small assets in an MVP; for production, move images to private object storage and store their URLs. The app currently limits each image upload to 900 KB.

## 6. Build and verify

```powershell
npm run build
```

Email login and CRUD need a reachable MongoDB connection. Google login is deferred and is not required for the current version. Browser print is used for Save as PDF; this is not a server-side PDF renderer. Validate GST treatment, access control, backups, production HTTPS and account-recovery email before using this for real accounting.
