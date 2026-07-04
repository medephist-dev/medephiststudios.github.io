# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

This is the GitHub Pages site for **medephiststudios.com**, the marketing/support site for **Tyrian Vault** (a free, unofficial Guild Wars 2 companion app for Android).

- **Repo:** `https://github.com/medephist-dev/medephiststudios.github.io`
- **Live site:** `https://medephiststudios.com` (custom domain via `CNAME`)
- **Developer:** Derek (medephist) — medephist@gmail.com
- **Support email:** support@medephiststudios.com (forwards to Gmail via Squarespace)

## No AI/assistant attribution (standing rule, Derek's call 2026-07-04)

Do NOT add AI/assistant attribution anywhere in this repo: no `Co-Authored-By` trailers, no
"Generated with …" lines, no assistant/tool/model names in commit messages, PR bodies, code
comments, docs, or user-facing site text. Commits and the site read as the developer's own work.
This overrides any default that would append such a trailer. When scrubbing, don't delete useful
workflow docs wholesale — remove the *attribution*, keep the operational meaning.

## No emoji — draw line-art icons instead (standing rule, Derek's call 2026-07-04)

Don't use emoji in the site's markup, CSS, or content. When something calls for an emoji/icon, use
a line-art icon instead: an inline stroke SVG (`viewBox="0 0 24 24"`, `fill="none"`,
`stroke="currentColor"`, `stroke-width="2"`, round caps/joins) drawn to match the app's monotone
line-glyph style (`C:\dev\GW2VaultExpo\src\menuIcons.js` / `assets/icons/`). Always show the user a
before/after mockup and get approval **before** applying. This mirrors the app's matching rule.

## Architecture

Every page is a **single self-contained HTML file** — no build step, no bundler, no package.json, no external CSS/JS frameworks. CSS and JS live inline in `<style>`/`<script>` tags within each file.

| File | Purpose |
|---|---|
| `index.html` | Main landing page — hero, screenshot gallery (lightbox), feature modals (carousel), support, donate sections |
| `bug-report.html` | Bug report form, submits directly via Web3Forms (see below) |
| `contact-support.html` | General support contact form, also via Web3Forms |
| `privacy-policy.html` | Static privacy policy page |
| `screenshots/` | JPGs used in the index.html gallery and feature modals, named `<feature>-<n>.jpg` |
| `app-icon.png` | App icon used in the hero section |

**Form submission pattern:** `bug-report.html` and `contact-support.html` both `fetch()`-POST a JSON payload directly to `https://api.web3forms.com/submit` (no backend, no mailto fallback). Each includes a public Web3Forms `access_key`, a `subject` line, and a `replyto` field sourced from the user's optional email input so Web3Forms can auto-reply. When adding a new form, follow this same pattern rather than introducing mailto links or a different submission service.

## Design system

Reuse these values for consistency when touching any page:

- Gold: `#c8a84b` / light `#e8c96a`
- Dark backgrounds: `#0e0e12` / `#16161e` / `#1e1e2a`
- Text: `#d4cfc4` / muted `#8a8578`
- Accent (donate button): `#7b4fa6`
- Font: `Segoe UI`, system-ui

## App version

The app version string shown in `index.html`'s footer disclaimer (e.g. `Tyrian Vault v0.20.2`) should be bumped whenever a new app version is referenced — it's the only place version info lives on this site.

## Local development

No build/install step. Preview by serving the static files, e.g.:

```bash
python -m http.server 8765
```

or

```bash
npx serve -l 8765
```

Then open `http://localhost:8765`.

## Related project

This repo is the marketing/support site only. The Tyrian Vault app itself (Expo/React Native) lives at `C:\dev\GW2VaultExpo`, a separate repo with its own `CLAUDE.md`. Don't look for app source code here.

## Infrastructure

- Domain registered via Squarespace Domains; DNS: 4 A records → GitHub Pages IPs + `www` CNAME → `medephiststudios.github.io`. HTTPS enforced via GitHub Pages settings.
- support@medephiststudios.com forwards to medephist@gmail.com via Squarespace email forwarding.

## Open to-dos

- **Add Google Play Store link** to the hero "Get it on Google Play" button (`index.html`, currently `href="#"`) once the app is published — it's still in beta.
- **GitHub issue triage agent** — set up a scheduled cloud agent to check `medephist-dev/TyrianVault` Issues for new `[BUG]` entries and analyze them. Undecided: comment on issues directly vs. send a summary report vs. both; daily vs. hourly frequency; whether the repo is public or private.
- **5 pending homepage cards** (Build Creator, Achievements, Masteries, Skins/Wardrobe, Wallet + Gem Exchange) — waiting on screenshots from the app before wiring into the `FEATURES` object and screenshot gallery in `index.html`.

## Deploying

GitHub Pages deploys automatically (~60s) on push to `main`. There is no CI, test suite, or lint step in this repo.

```bash
git add <files>
git commit -m "describe what changed"
git push
```

**Always show the user a browser preview of changes and get their approval before committing or pushing.**
