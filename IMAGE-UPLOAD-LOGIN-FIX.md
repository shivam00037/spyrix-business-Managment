# Login-required startup and invoice image uploads

## Startup and access control

- Opening `/` sends logged-out users to `/login`.
- The `/app/*` routes are guarded and redirect to login until email/password or configured Google sign-in succeeds.
- Guest/demo authentication and browser-saved demo records have been removed. Business records load through the signed-in API.

## Logo, QR, signature, and canvas images

- Upload from the Design Studio **Assets** tab, or use the clickable logo/QR/signature target directly on the invoice.
- Supported formats include PNG, JPG/JPEG, WEBP, GIF, BMP, AVIF, SVG, TIF/TIFF when the browser can decode them. Source files are limited to 18 MB and images are optimized for reliable local/business-workspace storage.
- Extra artwork can be uploaded from **Images you can place anywhere** or dragged from your computer onto the invoice. Use the move handle to position it; remove it with the close control.
- Image targets now remain visible on mobile. If the browser cannot decode a selected image, the invoice target reports that and lets you choose another file.
- Uploaded images update the live preview immediately. Save the template to sync the default design to MongoDB, or save/issue an invoice to store that invoice's design snapshot.

## Backend setup

Run `npm install` then `npm run dev` from the project root. Configure `server/.env` with `MONGODB_URI` and a strong `JWT_SECRET`. Configure Google OAuth only if using Google sign-in. Keep the terminal open while the frontend and backend run.
