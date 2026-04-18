# Jekyll Integration — Deployment Guide

These files replace the existing Jekyll templates with the new DAM Lab design.

## What's in this folder

```
jekyll/
  _includes/
    head.html          ← <head> tag (fonts, CSS, meta)
    header.html        ← site header + nav
    footer.html        ← site footer + social icons
  _layouts/
    default.html       ← base layout (wraps all pages)
    home.html          ← home page (hero + pubs + CTA)
    page.html          ← generic content page
    research.html      ← research interests + methods
    team.html          ← team grid (reads _data/settings.yml)
    publications.html  ← publications list (reads _data/publications.yml)
    news.html          ← news wrapper layout
    contact.html       ← contact page (reads _data/settings.yml contacts)
  assets/
    css/custom.css     ← all styles (replaces old custom.css)
    img/logo-mark.svg  ← hippocampal curl logomark
  index.md             ← home page (replaces existing)
  research.md          ← new research page
  people.md            ← team page (replaces existing)
  publications.md      ← publications page (replaces existing)
  news.md              ← news page with current content (replaces existing)
  contact.md           ← contact page (replaces existing)
```

## How to deploy

1. **Copy `_includes/`** files into your repo's `_includes/` folder (overwrite existing)
2. **Copy `_layouts/`** files into your repo's `_layouts/` folder (overwrite existing)
3. **Copy `assets/css/custom.css`** into `assets/css/` (overwrites existing)
4. **Copy `assets/img/logo-mark.svg`** into `assets/img/`
5. **Copy all `.md` files** into your repo root (overwrite existing)
6. **Remove** the old `assets/css/main.scss` import of Bootstrap if desired — the new design does not use Bootstrap
7. Commit and push:
   ```bash
   git add .
   git commit -m "New website design"
   git push
   ```

## Data files (unchanged)

These existing files **do not need to change** — the layouts read from them automatically:

- `_data/settings.yml` — people, alumni, social links, contacts
- `_data/publications.yml` — publication list (used on home + publications pages)

> **Note:** The `home.html` layout expects `_data/publications.yml` to exist with entries that have `year`, `title`, `journal`, and `authors` fields. If your publications data uses a different structure, the recent publications section on the home page may need adjusting.

## Fonts & external dependencies

- **Roboto** is loaded from Google Fonts via `_includes/head.html` — no local font files needed
- **Font Awesome** is no longer required (social icons are now inline SVG)
- **Bootstrap** is no longer required — you can remove it from `assets/libs/` to reduce load size

## Adding news posts

Edit `news.md` directly — add new `<div class="news-item">` blocks at the top.

Or, if you prefer Jekyll posts, switch `news.md` to loop over `site.posts` inside the news layout.
