# Kites Events — website

Static site. No build step, no dependencies to install.

## Structure

```
index.html        the whole page (markup + styles + logic)
support.js        runtime that mounts the page
image-slot.js     image placeholder element
images/           photography and logos
```

## Run locally

Open over HTTP (not `file://`, which blocks the module loads):

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Push to a repo

```bash
cd deploy
git init -b main
git add -A
git commit -m "Kites Events website"
git remote add origin git@github.com:<you>/<repo>.git
git push -u origin main
```

For GitHub Pages: Settings → Pages → Deploy from a branch → `main` / `/ (root)`.
The `.nojekyll` file is required there — without it Jekyll strips some assets.

## Deploy

Publish the contents of this folder as-is to any static host — GitHub Pages,
Netlify, Vercel, Cloudflare Pages, S3. No build command; the publish
directory is the repo root (or `deploy/` if you keep this folder nested).

Fonts (Cormorant Garamond, Marcellus, Karla) and the animation libraries (GSAP,
Lenis) load from CDNs,
so the deployed site needs network access. For a fully offline copy, use the
single-file export instead.

## Notes

- Light mode is the default; the sun/moon dial in the navbar switches to the
  night theme and the choice persists in `localStorage`.
- The opening curtain plays once per browser session (`sessionStorage` key
  `kites-curtain`) and is skipped under `prefers-reduced-motion`.
- Replace a photo by dropping a new file into `images/` under the same name.
