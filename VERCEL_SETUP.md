# Monali Driving School — Vercel via GitHub Guide

## What's in this zip

| File/Folder | Purpose |
|---|---|
| `api/index.mjs` | Express API server (fully bundled, runs as Vercel serverless function) |
| `api/pino-*.mjs`, `thread-stream-worker.mjs` | Logger support files (required alongside index.mjs) |
| `public/` | Built React website — Vercel serves this via its CDN at your root URL |
| `vercel.json` | Routing config — Vercel reads this automatically |
| `package.json` | Project metadata |

## How it works

```
yourdomain.com/api/*   →  api/index.mjs  (Express serverless function)
yourdomain.com/*       →  public/        (React SPA via Vercel CDN)
```

---

## Step 1 — Push to GitHub

Extract this zip, then push to a new GitHub repository:

```bash
git init
git add .
git commit -m "Initial deploy"
git remote add origin https://github.com/YOUR_USERNAME/monali-driving-school.git
git push -u origin main
```

---

## Step 2 — Connect to Vercel

1. Go to [vercel.com](https://vercel.com) → **Add New Project**
2. Click **Import** on your GitHub repository
3. **Important — leave all settings at their defaults** (do NOT change framework, build command, or output directory — `vercel.json` handles everything)
4. Click **Deploy**

---

## Step 3 — Add Environment Variables

1. Vercel Dashboard → your project → **Settings** → **Environment Variables**
2. Add:

| Name | Value |
|---|---|
| `DATABASE_URL` | Your PostgreSQL connection string |

3. Click **Save** → then go to **Deployments** → click **Redeploy**

### Free PostgreSQL options compatible with Vercel

| Option | How to get connection string |
|---|---|
| **Vercel Postgres** | Dashboard → Storage → Create Database → auto-sets `DATABASE_URL` |
| **Neon** (neon.tech) | Free tier → create project → copy connection string |
| **Supabase** (supabase.com) | Free tier → Settings → Database → Connection String |

---

## After deployment

| | |
|---|---|
| **Website** | `https://your-project.vercel.app` |
| **Admin panel** | `https://your-project.vercel.app/admin` |
| **Admin password** | `monali2024` ← **change this before sharing!** |

---

## Custom domain (optional)

1. Vercel Dashboard → your project → **Settings** → **Domains**
2. Add your domain (e.g. `monalidrivingschool.com.au`)
3. Update your domain DNS as Vercel instructs

---

## Auto-deploys

Once connected, every `git push` to your `main` branch automatically redeploys the site on Vercel. No manual steps needed.
