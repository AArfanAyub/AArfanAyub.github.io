# A.ArfanAyub — Personal Website

Personal site of **Ahmad Arfan bin Ayub** — environmental management student at UPM, community volunteer.

Built as a single static page. No frameworks, no build step, no external dependencies.

---

## 📁 What's in this repo

```
/
├── index.html          # the website (entry point)
├── imri/               # project page: IMRI, offline library management
├── serambi/            # project page: Serambi POS Pro, offline point of sale
├── assets/
│   ├── p-01…p-49.webp  # photos
│   ├── imri-*.png      # IMRI screenshots
│   └── fonts/          # Inter, self-hosted (woff2, 2 subsets)
├── _headers            # security + cache rules (Cloudflare Pages / Netlify)
└── robots.txt          # search engine rules
```

Each project page is fully self-contained: its own inline CSS, its own
`@font-face`, no shared stylesheet to break. They reuse the same CSS custom
properties so they match the main page.

---

## 🚀 Deploying

This is a plain static site — no build command needed.

### Cloudflare Pages (recommended — free forever, unlimited bandwidth)

1. Push this repo to GitHub
2. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
3. Select this repo
4. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/`
5. **Save and Deploy**

Your site goes live at `your-project.pages.dev`. The `_headers` file is applied automatically.

### GitHub Pages (alternative)

1. Repo → **Settings** → **Pages**
2. **Source:** Deploy from a branch → `main` → `/ (root)`
3. Save — live at `username.github.io/repo-name`

> Note: GitHub Pages ignores the `_headers` file, so security headers there come only from the `<meta>` tags in `index.html`.



---

## 🔒 Security

- Content-Security-Policy (no external scripts, styles, or CDNs)
- `X-Frame-Options: DENY` (clickjacking protection)
- `X-Content-Type-Options: nosniff`
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Permissions-Policy` (camera, microphone, location, etc. disabled)
- `Strict-Transport-Security` (forces HTTPS)
- Fully self-contained — zero third-party code

> **Fonts used to be the exception.** The page pulled Inter from
> `fonts.googleapis.com` via `@import`, which the CSP above blocked outright —
> so the whole site silently rendered in fallback fonts, and every visit made a
> request to Google that was refused. Inter is now served from `assets/fonts/`
> and the policy carries `font-src 'self'`. Zero third-party requests is now
> literally true, not aspirational.

## ⚡ Performance

- All images in **WebP** format (~37% smaller than JPEG)
- Hero image preloaded with high priority
- Offscreen gallery sections use `content-visibility: auto`
- All gallery images lazy-loaded
- Immutable 1-year cache on `/assets/*`

---

## ✏️ Editing

Just edit `index.html` — the CSS and JS are inline. Photos live in `assets/` and are named `p-01.webp` … `p-49.webp`.

To swap a photo: replace the file in `assets/` keeping the same name.

---

## 📬 Contact

- Email: <arfansec2@gmail.com>
- WhatsApp: 017-544 2335
- Instagram: [@arfanzzz.\_](https://instagram.com/arfanzzz._)

---

© 2026 Ahmad Arfan bin Ayub
