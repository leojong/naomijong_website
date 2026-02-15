# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static photography portfolio website for www.naomijong.com. Pure HTML/CSS/JavaScript with no framework or build system. Hosted on GitHub Pages.

## Development

No build step — files are served directly. Open `index.html` or `photos.html` in a browser to preview.

**Photo management:** After adding or removing images in `/photos`, run:
```
python update_photos.py
```
This regenerates `photos.json`, the manifest used by the gallery page. A Claude hook in `.claude/settings.json` auto-runs this before Bash commands.

## Architecture

- **index.html** — Homepage with hero background image and nav dropdown
- **photos.html** — Gallery page that dynamically loads images from `photos.json` (falls back to GitHub API). Includes lightbox with keyboard navigation (arrow keys, Escape)
- **style.css** — Global styles: nav, hero, dropdown, typography (Raleway via Google Fonts)
- **gallery.css** — Gallery-specific styles: CSS columns masonry layout, lightbox, staggered fadeUp animations
- **update_photos.py** — Python script that scans `/photos` for image files and writes `photos.json`
- **CNAME** — GitHub Pages custom domain config

## Git Rules

- Never commit automatically — at most stage files only. Wait for explicit user instruction to commit.

## Responsive Breakpoints

- Desktop: default (3-column gallery)
- Tablet (max-width 900px): 2-column gallery
- Mobile (max-width 600px): vertical nav, single-column gallery at 500px
