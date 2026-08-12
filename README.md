# SIP Panel Design Manual — Supersub

A static, single-page reference site for the Super Panel SIP connection details (sill, head, jamb, base, corners, penetrations, roof and foundation details). Built in Supersub brand colours, no build step required.

## Structure

```
index.html        one self-contained page (inline CSS/JS), hash-routed
images/           17 cropped detail drawings (WebP), extracted from the source PDF
vercel.json       clean URLs + long-cache headers for the images
```

## Run locally

```bash
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://localhost:3000` (or `:8080`).

## Deploy to Vercel

**Option A — CLI**

```bash
npm i -g vercel
cd sip-design-manual
vercel        # first deploy, follow the prompts
vercel --prod # promote to production
```

**Option B — GitHub + Vercel dashboard**

1. Push this folder to a new GitHub repo.
2. In the Vercel dashboard: New Project → Import the repo.
3. Framework preset: "Other" (no build command, no output directory needed — it's plain static files at the root).
4. Deploy.

**Option C — drag and drop**

On vercel.com, use the dashboard's "deploy a folder" flow and drop this whole `sip-design-manual` folder in.

## Editing content

All copy, callouts, and icons live in the `DETAILS` array near the top of the `<script>` block in `index.html`. Each entry maps to one drawing in `/images`. To add a new detail sheet:

1. Export the page as an image and save it into `images/` as `NN-slug.webp`.
2. Add a matching object to the `DETAILS` array with the same `num`/`slug`.

The "Browse all N connection details" heading count is driven automatically by `DETAILS.length`.
