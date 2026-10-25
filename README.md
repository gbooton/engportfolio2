# grahambooton.com

Personal portfolio. Plain HTML + one CSS file. No build step, no framework,
no dependencies.

## Files

| File | What it is |
|------|------------|
| `index.html` | The whole site on one page: About, Experience, Education, FSAE, Leadership, Skills, Fun, and Contact (footer). Edit prose here. |
| `resume.html` | Embeds `assets/Graham-Booton-Resume.pdf` inline, with "Open" / "Download" buttons. |
| `lebenslauf.html` | Embeds `assets/Graham-Booton-Lebenslauf.pdf` the same way. **This file doesn't exist yet** — drop it in `assets/` once it's finalized (see below). |
| `styles.css` | All styling, shared by every page. Colors and spacing are variables at the top (`:root`). You rarely need to touch this. |
| `assets/` | PDFs and any images. |
| `favicon.png` | The site icon — a "GB" monogram, white on transparent. Used as the browser-tab favicon *and* shown as a small mark in the top-right corner of the header on every page. Replace this one file to change both (keep it white/light, since it sits on a dark corner chip; and keep it small — a few hundred px square is plenty). |
| `CNAME` | Custom domain for GitHub Pages (`grahambooton.com`). |
| `.nojekyll` | Tells GitHub Pages to serve files as-is. |
| `404.html` | Shown for bad URLs. |

## Editing content later

Everything is plain text inside the HTML files:

- **Add a job or leadership role** — copy one `<details class="entry"> … </details>`
  block in the `PROFESSIONAL EXPERIENCE` or `CAMPUS LEADERSHIP & INVOLVEMENT`
  section of `index.html` and paste it at the top (newest first). Each one
  is a collapsible row: the `<summary>` (date + title, with the + icon) is
  always visible, and the bullets in `.details-body` show when it's clicked
  open.
- **Add an FSAE project** — copy one `<details class="entry">` block in the
  `FSAE PROJECTS` section (newest season first) and edit the season, name,
  and bullets. It's the same collapsible pattern as jobs and leadership roles.
- **Skills under a job, project, or role** — each entry has a
  `<ul class="tags" aria-label="Skills used">` under its bullets. Add or
  remove `<li>` chips there. (Every chip, here and in the Skills section,
  gets the same hover animation from `.tags li` in `styles.css`.)
- **Add a skill to the main Skills section** — add an `<li>` inside the
  relevant `<ul class="tags">` in that section.
- **Profile photo** — save a portrait photo (roughly 4:5, ~800px wide) as
  `assets/profile.jpg`. Until it exists, a dashed "Photo" placeholder shows
  on the home page.
- **Strava link** — the Fun section has a placeholder `href="#"` on the
  Strava link. Swap in your profile URL.
- **Résumé** — replace `assets/Graham-Booton-Resume.pdf` (keep the exact
  filename) and the preview/download on `resume.html` stay current
  automatically — no HTML edits needed.
- **Lebenslauf** — replace `assets/lebenslauf.pdf` (keep the exact filename)
  and `lebenslauf.html` picks it up automatically.
- **Contact info** — the Contact list is at the bottom of `index.html`. The
  phone number is intentionally not listed anywhere on the site.

The header (name, nav, and the small favicon mark in the corner) is
similar at the top of all three pages. If you change a nav link, check them
all.

## Publishing on GitHub Pages

1. Create a repo (any name; `grahambooton.github.io` works too) and push
   these files to the **root** of the default branch.
2. Repo **Settings → Pages** → Source: *Deploy from a branch* →
   Branch: `main`, folder: `/ (root)` → Save.
3. Under **Custom domain**, enter `grahambooton.com` and save. GitHub commits
   the `CNAME` file (already included) and provisions HTTPS.
4. At your DNS provider, point the domain at GitHub Pages:
   - Apex `grahambooton.com` → four `A` records:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     (and the matching `AAAA` records if you want IPv6)
   - `www` → `CNAME` record to `<your-user>.github.io`
5. Wait for DNS, then tick **Enforce HTTPS** in Settings → Pages.

Local preview: `python -m http.server` in this folder, then open
<http://localhost:8000>.
