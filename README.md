# Pramod Portfolio — Backend

Flask API for the contact form on your portfolio site. Saves every submission
to a database and emails you a notification.

## What it does

- `POST /api/contact` — validates and saves a submission, then emails you
- `GET /api/contact?key=YOUR_ADMIN_KEY` — lists all submissions (simple lead inbox)
- `GET /api/health` — health check for Railway

## 1. Run it locally (optional, to test first)

```bash
cd pramod-backend
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env          # then fill in real values in .env
python app.py
```

It runs on `http://localhost:5000`. Test it:

```bash
curl -X POST http://localhost:5000/api/contact \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","message":"Hello!"}'
```

## 2. Get a Gmail App Password (for email notifications)

Your normal Gmail password won't work with SMTP. Instead:

1. Go to your Google Account → Security → 2-Step Verification (turn it on if it isn't)
2. Go to Security → App Passwords
3. Create one for "Mail" → copy the 16-character password
4. Use that as `SMTP_PASS`

## 3. Deploy to Railway

1. Push this folder to a GitHub repo
2. On [railway.app](https://railway.app) → **New Project** → **Deploy from GitHub repo**
3. Select your repo. Railway detects the `Procfile` and deploys automatically.
4. **Add a database:** in your Railway project → **New** → **Database** → **PostgreSQL**.
   Railway automatically sets a `DATABASE_URL` variable — no extra config needed,
   the app picks it up automatically.
5. **Add environment variables** (Railway project → Variables tab):
   - `SMTP_USER`
   - `SMTP_PASS`
   - `NOTIFY_EMAIL`
   - `ADMIN_KEY`
6. Railway gives you a live URL like `https://your-app.up.railway.app`

## 4. Point the frontend at it

In `pramod-portfolio.html`, the contact form already posts to
`window.PRAMOD_API_URL`. Set that to your Railway URL:

```html
<script>
  window.PRAMOD_API_URL = "https://your-app.up.railway.app/api/contact";
</script>
```

That's it — form submissions will now save to your database and email you.

## Checking your leads

Visit:

```
https://your-app.up.railway.app/api/contact?key=YOUR_ADMIN_KEY
```

to see all submissions as JSON, without opening a database client.
