# Medephist Studios — Website Project

This is the GitHub Pages site for **medephiststudios.com**, the developer website for Tyrian Vault (a free unofficial Guild Wars 2 companion app for Android).

**Repo:** `https://github.com/medephist-dev/medephiststudios.github.io`  
**Live site:** `https://medephiststudios.com`  
**Developer:** Derek (medephist) — medephist@gmail.com  
**Support email:** support@medephiststudios.com (forwards to Gmail via Squarespace)

---

## Files

| File | Purpose |
|---|---|
| `index.html` | Main landing page — dark GW2-inspired theme, features, support, donate |
| `bug-report.html` | Bug report form — builds a mailto: URI and opens the user's email app |
| `privacy-policy.html` | Privacy policy (to be created from `privacy-policy.md`) |
| `app-icon.png` | App icon — used in the hero section of index.html |

---

## Design System

- **Gold:** `#c8a84b` / `#e8c96a` (light)
- **Dark backgrounds:** `#0e0e12` / `#16161e` / `#1e1e2a`
- **Text:** `#d4cfc4` / muted `#8a8578`
- **Accent (donate button):** `#7b4fa6`
- Font: `Segoe UI`, system-ui

All pages are single-file HTML — no external CSS/JS dependencies except what's inline.

---

## Pushing Changes

When files are updated, push with:

```bash
git add .
git commit -m "describe what changed"
git push
```

GitHub Pages deploys automatically within ~60 seconds of a push to `main`.

---

## To-Do

- [x] Create `privacy-policy.html` — done, no crash service (app collects no data)
- [x] Add donate link — Ko-fi: https://ko-fi.com/medephiststudios (index.html updated)
- [ ] Add Google Play Store link once app is published
- [x] `privacy-policy.html` link already present in footer

---

## Notes

- Domain registered via Squarespace Domains ($90 / 5 years)
- DNS: 4 A records → GitHub Pages IPs + CNAME www → medephiststudios.github.io
- HTTPS enforced via GitHub Pages settings
- Email forwarding: support@medephiststudios.com → medephist@gmail.com (Squarespace)
