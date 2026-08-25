# REAL HEALTH BRIDGE SYSTEM

This version includes real Cloudflare Pages Functions + D1 authentication and membership storage.

1. In your EXISTING Cloudflare Pages project, create D1 database `health-bridge-db`.
2. Run `schema.sql` in the D1 Console.
3. Copy the D1 database ID into `wrangler.toml` replacing `REPLACE_WITH_YOUR_D1_DATABASE_ID`.
4. Deploy the entire folder to the same Pages project.
5. Add a temporary environment variable `ADMIN_SETUP_KEY` in Cloudflare.
6. POST JSON to `/api/admin/bootstrap` with header `X-Setup-Key` and body containing first_name,last_name,email,password. Use a strong admin password (12+ chars).
7. After the admin is created, REMOVE `ADMIN_SETUP_KEY`.
8. Login at `/login.html`; admin can review applications at `/admin.html`.

Applications are stored in D1. Real passwords are hashed with PBKDF2-SHA-256 and sessions use HttpOnly Secure cookies.

Optional: configure Resend later if you want automatic email notifications to healthbridgegroup@outlook.com.
