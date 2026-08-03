# Davema Contact Form Backend (Vercel)

Serverless version of the backend — two endpoints:
- `POST /api/contact` — receives and emails the form submission
- `GET /api/health` — quick check that it's live

## Endpoints once deployed

If your Vercel project is at `https://davema-backend.vercel.app`, then:
- Contact form: `https://davema-backend.vercel.app/api/contact`
- Health check: `https://davema-backend.vercel.app/api/health`

## Environment variables (set these in the Vercel dashboard, not in a file)

- `SMTP_HOST` = smtp.gmail.com
- `SMTP_PORT` = 465
- `SMTP_USER` = your Gmail address
- `SMTP_PASS` = your Gmail App Password
- `CONTACT_RECEIVER` = where inquiries should land (can be same as SMTP_USER)
- `ALLOWED_ORIGIN` = your live site's URL once you know it (use `*` for now while testing)

## Notes

- No `express-rate-limit` here since serverless functions don't share memory between requests the same way a normal server does — the honeypot field still protects against basic bots.
- Nothing is stored in a database — mail-only, same as before.
