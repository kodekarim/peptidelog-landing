Build a premium, high-converting beta signup landing page for "Peptide Log" — a private GLP-1 and peptide injection tracker iOS app. Deploy to Cloudflare Pages.

## PRIVACY CLAIM — RESOLVED
Screenshots and in-app copy are now consistent: sync is real, optional, and goes to the user's own private iCloud account — never to a company server. Use this framing everywhere on the page and do not overclaim beyond it (e.g. don't say "no one but you can ever see it" unless Advanced Data Protection or HealthKit-level encryption is actually in place):
- Default state: private, on-device, no account, no sync.
- Optional state: user turns on iCloud sync → data goes to their own private iCloud account, not to Peptide Log's servers.
- In-app Settings copy to match: "iCloud Sync — Off by default. When enabled, your data syncs to your own private iCloud account, never to our servers."

## BRAND & POSITIONING
- App name: Peptide Log
- Tagline: "Track injections. Private by default." (sync is optional, so don't claim "nothing ever leaves your phone" as an absolute)
- Core value prop: No account, no cloud, no subscription for basic logging. Data stays on iPhone unless you turn on optional iCloud sync — and even then, it's your own private iCloud account, never a company server.
- Origin story: Built after losing 6 months of data to a cloud app.
- Target: GLP-1 patients (Ozempic, Wegovy, Mounjaro), biohackers, privacy-conscious users
- Credibility note: this is a solo-dev product — lean into that as a trust signal (a person, not a company harvesting health data), don't hide it or dress it up as a startup.

## DESIGN INSPIRATION (from 2026 top converters)
- Linear: dark mode, product UI as hero, no stock illustrations
- Lovable: interactive/demo feel in hero, concrete numbers
- Extreme Lounging: single focus, one CTA, minimal friction
- Langbase: short page, animated elements, waitlist opt-in

## REAL ASSETS TO USE (replace all placeholder divs with these)
Six actual App Store screenshots exist, each with its finalized title/subtitle baked into the design. Use them as-is — do not recreate the UI in CSS, use the images. Order matters (App Store only shows the first 2-3 before "see more," so lead with the trust story):

1. `screenshot-private-by-default.png` — "Private by Default" — "No account. No cloud. No tracking. Your data starts on your iPhone, period."
2. `screenshot-sync-if-you-want-it.png` — "Sync, If You Want It" — "Optional iCloud sync — your own private account, never our servers."
3. `screenshot-log-seconds.png` — "Log in Seconds" — "Pre-filled dose, smart site rotation, one tap to save."
4. `screenshot-never-miss-dose.png` — "Never Miss a Dose" — "Titration schedules and reminders, tuned to your plan."
5. `screenshot-every-shot-tracked.png` — "Every Shot, Tracked" — "Filter injections, weight, and side effects by medication."
6. `screenshot-ready-for-doctor.png` — "Ready for Your Doctor" — "Export as PDF or CSV in one tap."

## STRUCTURE (single page, scrollable)

### 1. HERO (above the fold, no scroll needed)
- Dark gradient background (#0F172A → #1E293B), subtle grain/noise texture like the screenshots (matches brand)
- Headline: "Track Your Injections. Private by Default."
- Subheadline: "No account. No subscription. Your GLP-1 data stays on your iPhone — sync to your own private iCloud account only if you choose to."
- ONE email input + CTA: "Join Beta — Get Early Access"
- Right side (desktop) / below fold (mobile): the `screenshot-private-by-default.png` phone mockup, slightly rotated like the source image, as the hero's actual visual — this is your product, not an illustration
- NO nav bar, no distracting links

### 2. PROBLEM SECTION
- Headline: "I lost 6 months of injection history to a cloud app."
- 3 pain-point cards (icon + one sentence, hover lift):
  - "Cloud apps lock you out" — data gone when they change pricing
  - "Subscriptions for basic logging" — $15/month just to track a shot
  - "Your health data on their servers" — who else sees it?

### 3. FEATURE SHOWCASE (replaces generic "solution cards" — use the real screenshots)
Alternating left/right layout, one row per screenshot, phone image on one side, headline + subcopy on the other. Copy matches the finalized screenshot titles/subtitles exactly, so the landing page and App Store listing tell the identical story:

1. Private by Default — `screenshot-private-by-default.png` — "No account. No cloud. No tracking. Your data starts on your iPhone, period."
2. Sync, If You Want It — `screenshot-sync-if-you-want-it.png` — "Optional iCloud sync — your own private account, never our servers."
3. Log in Seconds — `screenshot-log-seconds.png` — "Pre-filled dose, smart site rotation, one tap to save."
4. Never Miss a Dose — `screenshot-never-miss-dose.png` — "Titration schedules and reminders, tuned to your plan."
5. Every Shot, Tracked — `screenshot-every-shot-tracked.png` — "Filter injections, weight, and side effects by medication."
6. Ready for Your Doctor — `screenshot-ready-for-doctor.png` — "Export as PDF or CSV in one tap."

Staggered fade-in + slide-up on scroll (IntersectionObserver), subtle border glow on the active phone image.

### 4. SOCIAL PROOF / TRUST
- Headline: "Join the beta."
- Waitlist counter: only show if backed by a real number. If you don't have one yet, replace with a simple honest line: "Be one of the first 100 beta testers."
- Trust badges: "No data collection," "iOS native," "Privacy-first"
- One line, real: "Built by a solo dev who lost his own injection data to a cloud app that raised its prices."
- Optional trust footnote near the CTA: "Sync is optional and goes to your own private iCloud account — never our servers."

### 5. FINAL CTA
- Same email form as hero
- Headline: "Get early access. Be the first to try it."
- Sub: "Beta users get lifetime free access to future premium features."

### 6. FOOTER
- Links: Privacy Policy, Support, Contact (support@peptidelog.app)
- Minimal, no clutter

## TECH SPECS
- Single HTML file (index.html) + inline CSS, image assets referenced from `/assets/screenshots/`
- Mobile-first, responsive (320px–1440px)
- Dark mode only
- Google Fonts (Inter) only external dependency
- Email capture: form POST to placeholder endpoint (wire to ConvertKit/Beehiiv later)
- UTM parameter capture from URL into hidden field
- Smooth scroll; fade-in/slide-up on scroll
- Page load under 1 second target

## ANIMATIONS & INTERACTIONS
- Hero text: fade-in + slight Y translate on load (0.6s ease-out)
- Feature rows: staggered fade-in on scroll
- CTA button: subtle pulse glow every 4 seconds
- Counter (if real): animated count-up on scroll into view
- Input focus: border glow effect

## COPYWRITING RULES
- Every headline is an outcome, not a feature
- "GLP-1" only in context, not headlines
- Short sentences, one idea per section
- CTA buttons say what happens: "Join Beta," "Get Early Access" — never "Submit"
- Marketing copy must not claim anything the current app build doesn't actually do (see the fix-first note above)

## DELIVERABLES
1. index.html (complete, self-contained, real screenshots embedded)
2. privacy.html
3. support.html
4. README with Cloudflare Pages deployment instructions

## QUALITY CHECK
- Lighthouse target: 95+ Performance, 100 Accessibility
- Validate HTML
- Test on iPhone SE, iPhone 15 Pro Max, and desktop
- Confirm email input works with iOS autofill
- Confirm every privacy/sync claim on the page matches the actual current app behavior and the in-app Settings copy word-for-word
