# REDclip 小红夹 — marketing site

Static one-page site for **REDCLIP PTE. LTD.** No build step, no dependencies —
plain HTML/CSS/JS that any static host can serve.

## Pages

| File | Purpose |
| --- | --- |
| `index.html` | The one-pager: hero → scroll-scrubbed DNA journey → 11 services → platform showcase → contact |
| `login.html` | Client / Agent login chooser (switches theme in place, then hands off to the portals) |
| `platform.html` | Standalone "inside the platform" tour (not linked from the nav — the one-pager now covers it) |

Portals the login page hands off to:
- Client → `https://app.redclip.com`
- Agent → `https://go.redclip.com`

## Assets

Everything the site serves lives in `assets/`:

- `hero-scrub.mp4`, `hero2-loop.mp4`, `hero3-loop.mp4` — DNA clips, re-encoded all-intra
  (every frame a keyframe) so scroll-scrubbing is smooth. Don't re-compress without
  `-g 1` or scrubbing will stutter.
- `hero-poster.jpg` — first-frame poster
- `app-*.png` — product screenshots (transparent background)
- `reveal.jpg` — the collage revealed by the cursor spotlight on the hero

Raw source videos/screenshots are intentionally **not** committed (see `.gitignore`) —
they're large and only needed to regenerate the encodes.

## Local preview

Any static server works, e.g.:

```bash
python3 -m http.server 8642
```

then open <http://localhost:8642>.

## Deploying

The repo is deploy-ready as-is: no build command, output directory is the repo root.
On Vercel, import the repo and accept the defaults ("Other" framework preset).

## Editing content

Service copy, benefit lines, icons and screenshots are all defined in the `SERVICES`
array near the top of the `<script>` block in `index.html`. Adding a screenshot to a
service is one line: add `shot:'assets/your-file.png'` to that service's entry and it
replaces the placeholder card automatically.
