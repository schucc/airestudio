# Aire Studio

Static website for [www.airestudio.xyz](https://www.airestudio.xyz) — the home of **Aire Journal**, a private on-device AI journaling app for Mac.

## Pages

| URL | File |
|-----|------|
| `/` | `index.html` |
| `/aire/support/` | `aire/support/index.html` |
| `/aire/privacy/` | `aire/privacy/index.html` |

## Local preview

From the project root:

```bash
python3 -m http.server 8765
```

Then open [http://localhost:8765](http://localhost:8765).

## Project structure

```
index.html          Home page
style.css           Shared styles
main.js             Nav, scroll animations, FAQ toggles
aire/
  support/          FAQ and support contact guidance
  privacy/          Privacy policy
```

## Support

There is no web form on this site. Users are directed to:

- **In-app (recommended):** Setup → Help & Support → Report a Bug / Suggest an Improvement
- **Email:** [aire.support@airestudio.xyz](mailto:aire.support@airestudio.xyz)

## Deploy to Cloudflare

This site is static — no build step. Cloudflare can deploy it via **GitHub** (recommended for this repo) or **direct upload**.

### Option A: Deploy from GitHub (Workers & Pages)

1. Open the [Cloudflare dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create**.
2. Under **Ship something new**, choose **Connect GitHub**.
3. Authorize Cloudflare and select the **`schucc/airestudio`** repository (only that repo is needed).
4. On **Set up your application**, use these settings:
   - **Project name:** `airestudio`
   - **Build command:** *(leave empty — none required)*
   - **Deploy command:** `npx wrangler deploy`
   - **Root directory:** `/`
5. Click **Deploy** and wait for the pipeline to finish (Initializing → Cloning → Installing → Deploying).
6. When the build succeeds, Cloudflare assigns a temporary URL such as `https://airestudio.<account>.workers.dev`.

### Option B: Direct upload (no Git)

1. In the dashboard, go to **Workers & Pages** → **Create application** → **Pages** tab → **Upload assets** (Direct Upload).
2. Name the project and drag in the project folder or a zip of its contents.
3. The upload **must** include a top-level `index.html`, or the root URL will 404.
4. Click **Deploy site** to get a `*.pages.dev` URL.

### Connect custom domain (`airestudio.xyz`)

A successful build does **not** automatically use your custom domain. You still need to link it:

1. Open the **airestudio** project in **Workers & Pages**.
2. Go to the **Domains** tab.
3. Click **Add domain** (or **Set up a custom domain**).
4. Enter **`airestudio.xyz`** (and **`www.airestudio.xyz`** if you want both).
5. If DNS for `airestudio.xyz` is already on Cloudflare, records are added automatically. Otherwise, add the site under **Websites → Add a site**, point your registrar nameservers to Cloudflare, then return to the Domains tab.

After DNS propagates, the site is live at your custom domain.

### Other hosts

You can also deploy the repository root to any static host (S3, GitHub Pages, etc.). Ensure the host serves `index.html` for directory paths (e.g. `/aire/support/` → `aire/support/index.html`).

## License

© Aire Studio. All rights reserved.
