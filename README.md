# Cano Commission Consulting — Website

Static HTML site for **commissionconsulting.com**. Lightweight, fast, no framework.

## Files

```
commission-consulting/
├── index.html          Single-page landing (hero, pain, services, approach, work, results, contact)
├── about.html          Ed's bio, career timeline, credentials
├── README.md           This file
├── CNAME               Domain file for GitHub Pages (created at deploy time)
└── assets/
    ├── logo.svg        Horizontal lockup (header + footer)
    ├── logomark.svg    Square mark (favicon, social)
    ├── styles.css      All site styles
    └── ed-cano.jpg     Headshot — DROP YOUR PHOTO HERE (about page will fall back to placeholder if missing)
```

## TODO before going live

- [ ] Drop headshot photo at `assets/ed-cano.jpg` (recommend ~800×1000 px, 4:5 aspect)
- [ ] Set up email forwarding for `Edward.cano@commissionconsulting.com` (GoDaddy free email forwarding, see step 5 below)
- [ ] Decide: GitHub Pages + custom domain (recommended) OR GoDaddy WordPress hosting
- [ ] Once Commission Engine has a screenshot, drop it in `assets/` and link from the demo card
- [ ] Add real screenshots of Income Calculator, Genealogy Viewer, KPI Dashboard to replace the icon placeholders in the demo cards

## Local preview

Just open `index.html` in your browser. No build step.

For a slightly nicer local preview with proper paths, run a one-line static server from this folder:

```powershell
# Python (if installed)
python -m http.server 8000
# then open http://localhost:8000

# OR Node (if installed)
npx serve .
```

## Recommended deploy: GitHub Pages + GoDaddy DNS

Free hosting, fast, HTTPS automatic, matches your existing pattern (mexcano.github.io).

### Step 1 — Create the GitHub repo

1. Go to https://github.com/new
2. Repo name: `commission-consulting` (under the `mexcano` account)
3. Public, no README (we already have one)
4. Create repository

### Step 2 — Push the site

From this folder in PowerShell:

```powershell
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/mexcano/commission-consulting.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. Repo → Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: `main` / folder: `/ (root)` → Save
4. Wait ~30 seconds. Site will be live at `https://mexcano.github.io/commission-consulting/`

### Step 4 — Point commissionconsulting.com at GitHub Pages

**In GitHub:** Settings → Pages → Custom domain → enter `commissionconsulting.com` → Save. (This auto-creates a `CNAME` file in the repo.)

**In GoDaddy DNS** (My Products → commissionconsulting.com → DNS):

Add these **A records** for the apex domain (`@`):

```
Type: A   Name: @   Value: 185.199.108.153   TTL: 1 Hour
Type: A   Name: @   Value: 185.199.109.153   TTL: 1 Hour
Type: A   Name: @   Value: 185.199.110.153   TTL: 1 Hour
Type: A   Name: @   Value: 185.199.111.153   TTL: 1 Hour
```

Add a **CNAME record** for `www`:

```
Type: CNAME   Name: www   Value: mexcano.github.io   TTL: 1 Hour
```

**Remove or replace** any existing A records pointing to GoDaddy's parking page or the WordPress IP. (Keep MX records for email — those are unrelated.)

DNS propagates in ~5–60 minutes. Once live, GitHub Pages will auto-issue HTTPS within ~15 min.

### Step 5 — Email forwarding (free with GoDaddy)

To receive `Edward.cano@commissionconsulting.com`:

1. GoDaddy account → My Products → **Email & Office** → **Email Forwarding**
2. Set up: `Edward.cano@commissionconsulting.com` → forwards to `thecanoexperience@gmail.com`
3. Optional second forward: `info@commissionconsulting.com` → same Gmail

This is free and lets you reply from Gmail using the custom address (Gmail → Settings → Accounts → Send mail as → add `Edward.cano@commissionconsulting.com`).

## Updating content

Edit `index.html` or `about.html` directly, commit, push:

```powershell
git add .
git commit -m "Update copy"
git push
```

GitHub Pages auto-rebuilds in ~30 sec.

## Alternative: GoDaddy WordPress hosting

Not recommended (slower, less on-brand for an AI-builder positioning, more maintenance), but if preferred:

1. Use the WordPress page builder to recreate the structure
2. Or install a plugin like **Custom HTML** and paste each page's body
3. Or replace the WordPress install with a static-site plugin

The GitHub Pages route ships in 30 minutes total. WordPress will take a half-day.

## Notes

- All copy is final draft. Tweak as you read it; nothing is locked.
- The headshot is the only blocking asset for the about page to look complete.
- Once the Commission Engine demo is ready, swap the "Coming Soon" badge for "Live" and link it.
- Site is fully responsive (mobile + tablet + desktop) and should pass Lighthouse 95+ on performance/accessibility.
