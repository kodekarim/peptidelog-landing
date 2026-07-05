# Peptide Log — Beta Landing Page

Premium beta signup landing page for **Peptide Log**, a private GLP-1 and peptide injection tracker for iOS.

## Files

```
landing-page/
├── index.html          # Main landing page
├── privacy.html        # Privacy policy
├── support.html        # Support & FAQ
├── assets/
│   └── screenshots/    # App Store screenshots (used in page)
├── resources/          # Source screenshot files
└── landing-page-prompt.md
```

## Local preview

Serve the folder with any static file server:

```bash
cd PT_SD/landing-page
python3 -m http.server 8080
```

Open [http://localhost:8080](http://localhost:8080).

Or open `index.html` directly in a browser (relative asset paths work).

## Deploy to Cloudflare Pages

### Option A — Git integration (recommended)

1. Push this repo (or a subtree) to GitHub/GitLab.
2. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Select the repository and configure:
   - **Production branch:** your main branch
   - **Build command:** *(leave empty — static site)*
   - **Build output directory:** `PT_SD/landing-page`
4. Click **Save and Deploy**.

Cloudflare serves the site at `*.pages.dev`. Add a custom domain under **Custom domains** (e.g. `peptidelog.app`).

### Option B — Direct upload (Wrangler CLI)

```bash
npm install -g wrangler
cd PT_SD/landing-page
wrangler pages deploy . --project-name=peptide-log
```

First run creates the project; subsequent deploys update it.

### Option C — Drag-and-drop

1. Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** → **Upload assets**.
2. Zip the contents of `landing-page/` (not the folder itself — `index.html` should be at the zip root).
3. Upload and deploy.

## Wire up email capture

Forms currently POST to a placeholder endpoint and show a client-side success message. To connect a provider:

### ConvertKit

1. Create a form in ConvertKit and copy the form action URL.
2. Replace `https://placeholder.convertkit.com/subscribe` in both forms in `index.html`.
3. Match hidden field names to ConvertKit's expected fields (e.g. `email_address`).

### Beehiiv

1. Create an embed/form in Beehiiv and use their POST endpoint.
2. Update form `action` and field names accordingly.

UTM parameters (`utm_source`, `utm_medium`, `utm_campaign`, `utm_term`, `utm_content`) are captured from the URL into hidden fields automatically.

## Custom domain (Cloudflare)

1. Add the domain to Cloudflare DNS (or transfer).
2. In Pages project → **Custom domains** → add `peptidelog.app` and `www.peptidelog.app`.
3. Cloudflare provisions SSL automatically.

## Quality checklist

- [ ] Lighthouse: 95+ Performance, 100 Accessibility
- [ ] Test on iPhone SE (320px), iPhone 15 Pro Max, desktop 1440px
- [ ] Confirm iOS email autofill works (`autocomplete="email"`)
- [ ] Verify all privacy/sync claims match in-app Settings copy
- [ ] Replace placeholder form endpoint before launch

## Privacy claims (must stay in sync with app)

- Default: private, on-device, no account, no sync.
- Optional: iCloud sync → user's own private iCloud account, never Peptide Log servers.
- In-app Settings: *"iCloud Sync — Off by default. When enabled, your data syncs to your own private iCloud account, never to our servers."*
