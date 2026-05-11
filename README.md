# WasteLess Legal Documents

Static HTML for the WasteLess Privacy Policy and Terms of Use, designed to be hosted on GitHub Pages and linked from the iOS paywall and App Store Connect metadata.

## Files

- `index.html` — landing page that links to both documents
- `privacy.html` — Privacy Policy
- `terms.html` — Terms of Use

## Before publishing — fill in the placeholders

Search `privacy.html` and `terms.html` for these bracketed tokens and replace them:

- `[COMPANY_NAME]` — your LLC's legal name (or your own name if not incorporated yet)
- `[CONTACT_EMAIL]` — the email address users should write to for privacy/legal questions
- `[EFFECTIVE_DATE]` — today's date in a format like "May 10, 2026"
- `[STATE_OR_COUNTRY]` — the US state (or country) whose laws govern the agreement, e.g. "the State of California" or "the State of New York"

Quick find/replace from the terminal:

```bash
cd "wasteless-legal"
# Replace these with your real values
sed -i '' 's/\[COMPANY_NAME\]/YourLLC LLC/g' privacy.html terms.html
sed -i '' 's/\[CONTACT_EMAIL\]/hello@yourdomain.com/g' privacy.html terms.html
sed -i '' 's/\[EFFECTIVE_DATE\]/May 10, 2026/g' privacy.html terms.html
sed -i '' 's/\[STATE_OR_COUNTRY\]/the State of California/g' terms.html
```

## Hosting on GitHub Pages

1. Create a new public GitHub repo (e.g. `wasteless-legal`).
2. Push the contents of this folder to the repo's `main` branch.
3. In the repo's **Settings → Pages**, set the source to `main` branch, `/ (root)` folder, and save.
4. After ~1 minute, the docs are live at:
   - `https://<your-github-username>.github.io/wasteless-legal/`
   - `https://<your-github-username>.github.io/wasteless-legal/privacy.html`
   - `https://<your-github-username>.github.io/wasteless-legal/terms.html`

## After publishing — update the app and App Store Connect

1. **iOS app** — open `WasteLess/WasteLess/WasteLess/PaywallView.swift` and update the two URL constants at the top of the file (`privacyPolicyURL` and `termsOfUseURL`) with your live GitHub Pages URLs.
2. **App Store Connect** — enter the Privacy Policy URL in the App Privacy section. The Terms of Use URL goes in the EULA field if you're using a custom EULA, otherwise Apple's standard EULA applies.

## A note on legal robustness

These templates are written in plain language and cover the basics, but they are not a substitute for review by a lawyer. For TestFlight beta they're sufficient. Before App Store launch — especially with paid subscriptions — consider having an attorney review them, or use a generator service like Termly or iubenda that produces policies tailored to your data practices.
