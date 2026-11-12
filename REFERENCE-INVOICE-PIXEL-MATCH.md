# Reference invoice recreation update

The default Xenmark invoice canvas has been rebuilt against the reference image supplied on 12 November 2026. The desktop version uses the same top brand block, large maroon invoice title band, Bill To / Bill By cards, four-part date strip, six-row line-item table, payment + totals columns, bottom services ribbon and two-tone footer. Text and line values remain editable directly on the canvas; the logo, payment QR and signature areas remain uploadable.

The template preview uses the uploaded reference's cropped logo and QR image as replaceable sample assets so the first preview resembles the screenshot. This sample QR is for template preview only: a new invoice without a saved QR still asks the user to upload their own payment QR. The cropped sample logo similarly yields to a logo uploaded by the user.

The supplied screenshot has a small accounting inconsistency: its six displayed line amounts add up to ₹46,500, while its printed subtotal reads ₹46,000. To reproduce the reference faithfully, the untouched template preview displays the screenshot's printed summary (₹46,000 subtotal, ₹2,000 discount, ₹7,920 GST and ₹51,920 total). If a user changes an item amount, quantity, discount or tax, the preview switches to the calculated values. Normal invoice creation always calculates totals from its actual line items.

A one-time design revision migration upgrades previous Xenmark saved defaults from revision 2 to revision 3 while preserving the user's own uploaded assets and saved business details.

## Run

From the extracted project root in PowerShell:

```powershell
npm install
npm run dev
```

If MongoDB or Google sign-in is enabled, configure `server/.env` and `client/.env` using the included `.env.example` files. `npm run dev` starts frontend and backend without requiring the `concurrently` executable.
