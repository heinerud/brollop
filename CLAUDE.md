# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the site

Just open `index.html` directly in a browser — no server, no build step.

## Architecture

Pure HTML + CSS + vanilla JS. Single page, no dependencies, no backend.

- `index.html` — entire site
- `style.css` — all styles
- `CNAME` — sets custom domain to `lisaochjoel.heinerud.se` for GitHub Pages
- `.github/workflows/pages.yml` — deploys to GitHub Pages on push to `master`

## Page sections (in order)

1. **Nav** — sticky, links to `#information`, `#osa`, `#tal`
2. **Hero** — names + dates
3. **Välkommen** — intro text + photo (`photo.jpg`)
4. **Information** — three-day program, venue cards, place cards (Herrgården/Kvarnen with `herrgarden.jpg`/`kvarnen.jpg`), dress code, embedded Google map
5. **Boende** — accommodation info + nearby alternatives
6. **OSA** — RSVP form
7. **Tal & framträdanden** — speeches form
8. **Kontakt** — phone numbers + toastmaster email

## Changing the color palette

All colors are CSS custom properties in the `:root` block at the top of `style.css`. Change them there and everything updates automatically.

## Form submission

Forms build a pre-filled `mailto:` URL and open the user's email client — no backend.

- OSA sends to `lisaochjoel@heinerud.se` (`RECIPIENT_OSA` in the script)
- Speeches sends to `toastmaster@heinerud.se` (`RECIPIENT_TAL` in the script)

## Dynamic guest list (OSA form)

`addPerson()` creates a person card with name, närvaro radio buttons, and a matpreferenser field. Cards are indexed via `data-index` and collected by `collectPersoner()` before the mailto is built. The first card is not removable.

## Images

Drop these files into the repo root to replace placeholders:
- `photo.jpg` — couple photo in the welcome section
- `herrgarden.jpg` — Herrgården in the information section
- `kvarnen.jpg` — Kvarnen in the information section
