# Splittry legal site

Public, static legal pages intended for GitHub Pages.

- `privacy.html` — Privacy Policy
- `terms.html` — Terms of Service
- `delete-account.html` — account deletion instructions

Replace the contact email and operator details with the final legal entity before publishing. The app's Privacy Policy / Terms / account deletion URLs should point at these pages.

## Publish as a public repo + GitHub Pages

These pages are intentionally separate from the app source so the public legal
site contains no application code or credentials.

If GitHub CLI is authenticated:

```bash
cd legal-site
git init -b main
git add .
git commit -m "Add Splittry legal pages"
gh repo create splittry-legal --public --source=. --remote=origin --push

gh api -X POST repos/hotdogs312/splittry-legal/pages \
  -f build_type=legacy \
  -F source[branch]=main \
  -F source[path]=/
```

Then use:

- `https://hotdogs312.github.io/splittry-legal/privacy.html`
- `https://hotdogs312.github.io/splittry-legal/terms.html`
- `https://hotdogs312.github.io/splittry-legal/delete-account.html`

GitHub Pages may take a minute to become available after the first deployment.
Replace the contact email/operator details before submitting the URL to Google
Play.
