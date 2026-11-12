# Intro page and email/password login

## Requested navigation flow

1. Open `http://localhost:5173/` to see the SPYRIX INVOICE intro page.
2. Use **Get Started** or **Login** to open the login page.
3. Sign in with email/password or use **Create account**. Successful authentication opens `/app/dashboard`.
4. Protected `/app/*` routes redirect unauthenticated visitors to login.

The root route renders the existing `IntroPage`; the original intro design is preserved.

## Google sign-in is deferred

Google sign-in is intentionally not shown in the current login page. You do not need `VITE_GOOGLE_CLIENT_ID` or `GOOGLE_CLIENT_ID` to run email/password login. Google sign-in can be configured in a later update.

## Run

From the project root, configure `server/.env` using `server/.env.example`, ensure MongoDB is running, then run:

```powershell
npm install
npm run dev
```
