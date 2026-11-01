# aarfanayub.github.io

Hi — I'm Arfan. This is my portfolio site.

It's one static HTML file plus a few project pages. No framework, no build step,
no dependencies. I edit the file, push to `main`, and it's live about a minute
later.

I kept it static on purpose. It's a portfolio — it should load fast on a phone
with one bar of signal, and it should still open in five years without me
touching a lockfile. A plain HTML file does both.

## What's here

```
index.html        the site — HTML, CSS and JS all inline
imri/             IMRI — offline library system
serambi/          Serambi POS Pro — offline point of sale
nexus/            NEXUS — offline ERP + CRM
assets/
  p-01…p-49.webp  photos
  imri-*.png      IMRI screenshots
  nexus-icon.png  NEXUS icon (also the favicon)
  fonts/          Inter, self-hosted
_headers          security + cache headers (Cloudflare / Netlify)
robots.txt
```

Each project page is its own file with its own inline CSS. No shared
stylesheet. That's deliberate: a bad edit on one project page can't break the
homepage, and I never have to worry about a class name colliding. They all use
the same CSS variables, so they still look like one site.

## Running it locally

Nothing to install. You can open `index.html` straight in a browser. If you
want it served properly (fonts, relative paths, headers), run this from the
repo root:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.

## Deploying

Live at **aarfanayub.xyz** (Cloudflare in front of GitHub Pages) and
**aarfanayub.github.io**.

GitHub Pages builds straight from `main`, so pushing is the whole deploy. Give
it a minute.

If you're using this as a starting point for your own site, Cloudflare Pages
works well too: connect the repo, leave the build command empty, set the output
directory to `/`. It picks up `_headers` automatically. GitHub Pages ignores
`_headers`, so there the security headers come from the `<meta>` tags in
`index.html` instead.

## Notes to myself

- **No third-party requests.** Fonts are self-hosted, there's no analytics and
  no CDN. The CSP is strict (`default-src 'none'`), so everything on the page is
  either inline or same-origin. If I add something that needs a new source, I
  have to add it to the policy — otherwise it silently fails, which is the whole
  point of having the policy.
- **Images** are WebP and lazy-loaded; the hero is preloaded. Photos are
  `p-01.webp` … `p-49.webp` in `assets/`.
- **Editing** means editing `index.html`. The CSS is in the `<style>` block near
  the top, the JS is at the bottom. To swap a photo, drop a new file into
  `assets/` with the same name.

## Contact

- arfansec2@gmail.com
- WhatsApp 017-544 2335
- Instagram [@arfanzzz.\_](https://instagram.com/arfanzzz._)

---

© 2026 Ahmad Arfan bin Ayub
