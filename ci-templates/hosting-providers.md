# Deploying Glyphrig on Other Static Hosts

Because all site generation lives inside `@glyphrig/cli`, your bookmark repository needs **no `package.json` or framework boilerplate**. Any CI or static host that can run Node 22 works out of the box.

## Cloudflare Pages

- **Build command:** `npx --yes @glyphrig/cli@0 build --base /`
- **Build output directory:** `dist`
- **Node version env var:** `NODE_VERSION=22`

## Netlify

- **Build command:** `npx --yes @glyphrig/cli@0 build --base /`
- **Publish directory:** `dist`
- **Environment variables:** `NODE_VERSION=22`

## Vercel

- **Build Command:** `npx --yes @glyphrig/cli@0 build --base /`
- **Output Directory:** `dist`
- **Install Command:** `true` *(skip install since there is no `package.json`)*

## Local Preview & Validation

```bash
# Validate Markdown files and glyphrig.config.yaml
npx @glyphrig/cli validate

# Start live local preview server
npx @glyphrig/cli dev
```
