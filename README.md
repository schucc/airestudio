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

## Deploy

This is a static site — deploy the repository root to any static host (S3, Cloudflare Pages, GitHub Pages, etc.). No build step required.

Ensure the host serves `index.html` for directory paths (e.g. `/aire/support/` → `aire/support/index.html`).

## License

© Aire Studio. All rights reserved.
