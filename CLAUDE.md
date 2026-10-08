# emilysilcock.com

Personal academic website. Plain HTML + one CSS file, served by GitHub Pages at
https://emilysilcock.com. No build step, no framework — edit the HTML directly.

## Layout

- `index.html` — home (bio, photo, CV link)
- `research.html`, `data-and-resources.html`, `contact.html` — served at `/research` etc.
  (GitHub Pages serves `foo.html` at `/foo`, which keeps the old Google Sites URLs working)
- `privacy.html` — **must stay at `/privacy`**: it is the privacy-policy URL registered for
  the `fasrc-rclone` Google OAuth client (rclone access on FASRC). Don't move, rename, or
  delete it. It is deliberately not linked from the nav — it's only for Google.
- `home.html` — redirect from the old Google Sites `/home` URL to `/`
- `404.html` — GitHub Pages' not-found page
- `style.css` — all styling; `images/` — photos
- `CNAME` — custom domain for GitHub Pages; don't delete

## Conventions

- The header nav is duplicated in every page (there is no footer). When changing it, update every
  `.html` file (except `home.html`) and set `aria-current="page"` on the current page's link.
- Publications use `<ul class="pubs">` with `<span class="title">&ldquo;…&rdquo;</span>`,
  then authors/venue, then `[Arxiv]`-style links in `<span class="links">`. Newest first.
- Every page links `/style.css?v=N`. After editing `style.css`, bump `N` in all pages, or
  browsers/GitHub's CDN keep serving the old stylesheet for ~10 minutes.
- Use internal links without `.html` (`/research`, not `/research.html`).

## Preview & deploy

- Preview locally: `python -m http.server 8000` in this folder, then open http://localhost:8000
  (opening the files directly won't resolve the root-relative `/style.css` links). The local
  server doesn't do GitHub Pages' extensionless lookup, so visit `/research.html` etc. directly.
- Deploy: commit and push to `main`; GitHub Pages publishes within about a minute.
