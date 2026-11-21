# Glyphrig Bookmark Template

A data-only starter repository for **[Glyphrig](https://github.com/Glyphrig/Glyphrig)** — synchronize a chosen browser bookmark folder two-way across Chrome, Firefox, and Firefox for Android, and publish a fast static bookmark directory via Astro + Pagefind.

## Repository Contents

```text
├── bookmarks/              # Folder-mirrored Markdown files (bookmarks/**/README.md)
├── glyphrig.config.yaml    # Site title, theme accent, enrichment, and optional PWA Quick Add
├── .github/workflows/
│   └── deploy.yml          # GitHub Actions -> GitHub Pages (with cached link enrichment)
└── ci-templates/           # Ready-to-use workflows for GitLab, Forgejo/Codeberg, Cloudflare, etc.
```

No `package.json` or Astro config is required here — CI invokes `npx @glyphrig/cli build` directly.

---

## 2-Minute Setup

1. **Create your repo:** Click **Use this template** on GitHub (or clone into GitLab / Codeberg).
2. **Customize config:** Edit [`glyphrig.config.yaml`](./glyphrig.config.yaml) with your site title, bio, and accent color.
3. **Enable Pages:**
   - **GitHub:** Open **Settings -> Pages -> Build and deployment -> Source** and select **GitHub Actions**. Pushing to `main` (or running the workflow manually) builds and deploys your site automatically.
   - **GitLab / Codeberg / Cloudflare / Netlify / Vercel:** Copy the matching file from [`ci-templates/`](./ci-templates/).
4. **Connect the Glyphrig Browser Extension:**
   - Create a dedicated bookmark folder in Chrome or Firefox (e.g. `Public Bookmarks`).
   - Open Glyphrig **Settings**, configure your repository (`owner`, `repo`, branch `main`, folder `bookmarks`), authenticate via **GitHub OAuth Device Flow** or a scoped **Personal Access Token**, pick your bookmark folder, and confirm the **First-Sync Dry-Run Preview**.

## Bookmark Markdown Format

Each folder maps to `bookmarks/<folder>/README.md`:

```markdown
---
title: Developer Tools
order: 0
description: Languages, docs, and engineering references.
---

Optional hand-written intro prose rendered at the top of the folder page.

- [MDN Web Docs](https://developer.mozilla.org) — Authoritative web reference `#docs` `#web` <!-- glyphrig: added=2026-11-20 -->
```

- Hand-edited notes, `#tags`, frontmatter descriptions, and intro prose are preserved across browser syncs.
- Browser sync automatically blocks non-public URLs (`localhost`, LAN IPs, `file://`, `chrome://`), embedded credentials/tokens, and tracking parameters (`utm_*`, `fbclid`, etc.).
