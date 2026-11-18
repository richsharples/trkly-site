# trkly-site

Landing page for [trkly.app](https://trkly.app), served by Cloudflare Pages (project `trkly-site`). Static HTML/CSS, no build step. Colours, type and spacing come from the Trkly design system (tokens mirrored in `assets/site.css`).

## Files
- `index.html` — the one-page site
- `assets/site.css` — styles and design tokens
- `favicon.svg` — the Trkly mark
- `CNAME` — custom domain (`trkly.app`)
- `.nojekyll` — serve files as-is

## Deploy
Push to `main` → GitHub Actions deploys to the Cloudflare Pages project `trkly-site` (pull requests get a preview URL).

One-time setup:
1. Repo → Settings → Secrets and variables → Actions: secret `CLOUDFLARE_API_TOKEN`, variable `CLOUDFLARE_ACCOUNT_ID` (same values as the `trkly` app repo).
2. trkly.app's DNS must be a Cloudflare zone (nameservers at GoDaddy pointed to Cloudflare); an apex domain can't be attached to Pages otherwise.
3. Cloudflare → Workers & Pages → `trkly-site` → Custom domains: add `trkly.app` and `www.trkly.app` (then redirect www → apex with a Redirect Rule or bulk redirect).
4. Repo → Settings → Pages → turn GitHub Pages off once trkly.app shows the Cloudflare deploy. `CNAME` and `.nojekyll` are GitHub Pages leftovers and can then be deleted.

The app lives separately at `app.trkly.app`; "Sign in" links there.

## Beta sign-up
"Request an invite" opens the Google Form (owned by rich.sharples@softwhere.org); responses go to its linked Sheet. The form must allow responses from outside softwhere.org.

## Changing the styles

Browsers keep `assets/site.css` for a week. After editing it, change the `?v=` number on the stylesheet link in every page (`index.html`, `changelog/`, `privacy/`), so visitors get the new styles straight away. Any new value works; the first 8 characters of `sha1sum assets/site.css` is the convention.

New top-level folders must also be added to the copy step in `.github/workflows/deploy.yml`, or they won't be deployed.

## Changelog

`changelog/index.html` (served at trkly.app/changelog/). Newest entry at the top. Add an entry whenever a
user-facing change ships: date, a short headline, one plain-English sentence, then bullets about what people
will notice (not how it was built).
