# trkly-site

Landing page for [trkly.app](https://trkly.app), served by GitHub Pages. Static HTML/CSS, no build step. Colours, type and spacing come from the Trkly design system (tokens mirrored in `assets/site.css`).

## Files
- `index.html` — the one-page site
- `assets/site.css` — styles and design tokens
- `favicon.svg` — the Trkly mark
- `CNAME` — custom domain (`trkly.app`)
- `.nojekyll` — serve files as-is

## Deploy
1. Push to `main` of `trkly-site`.
2. Settings → Pages → Source: *Deploy from a branch*, `main` / root.
3. DNS for trkly.app (apex): A records to 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 (and AAAA 2606:50c0:8000::153 … 8003::153). Optional `www` CNAME → `<user>.github.io`.
4. Tick **Enforce HTTPS** once the certificate is issued (.app domains only work over HTTPS).

The app itself lives at `app.trkly.app` (Cloudflare Pages), so add that CNAME separately.

## Beta sign-up
The form posts to the URL in `data-endpoint` on `#beta-form`. Leave it empty and the form just says invites open soon. To collect emails, create a form (e.g. Formspree) and paste its endpoint there.
