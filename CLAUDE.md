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
- Publications use `<ul class="pubs">`; each `<li>` is `<span class="title">` (no quotes),
  then `<span class="meta">With …. Venue, Year.</span>` (more `.meta` lines allowed, e.g.
  press coverage), then `<span class="links">` holding bare `<a>`s (`arXiv`, `Dataset`,
  `Website`…; no brackets, no raw URLs as link text). Newest first.
- Label/value details (the contact page) use `<dl class="details">`. The home page keeps
  affiliations and the CV link as prose, deliberately — Emily didn't like them as a list.
- Every page links `/style.css?v=N`. After editing `style.css`, bump `N` in all pages, or
  browsers/GitHub's CDN keep serving the old stylesheet for ~10 minutes.
- Use internal links without `.html` (`/research`, not `/research.html`).

## Domain & DNS

Registrar/DNS: Squarespace Domains (migrated from Google Domains), signed in with Emily's
gmail Google account. Domain expires 2027-02-17. Records that must stay:
- `@` A → 185.199.108.153 / .109 / .110 / .111 (GitHub Pages); `www` CNAME → `emilysilcock.github.io`
- `_github-pages-challenge-emilysilcock` TXT — GitHub Pages verified-domain record (anti-takeover)
- `4vlw3l7zmnsf` CNAME → `…dv.googlehosted.com` — Google domain verification (likely what the
  fasrc-rclone OAuth client relies on)

## Preview & deploy

- Preview locally: `python -m http.server 8000` in this folder, then open http://localhost:8000
  (opening the files directly won't resolve the root-relative `/style.css` links). The local
  server doesn't do GitHub Pages' extensionless lookup, so visit `/research.html` etc. directly.
- Deploy: commit and push to `main`; GitHub Pages publishes within about a minute.
