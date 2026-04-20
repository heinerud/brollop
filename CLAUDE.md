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

OSA submits to Google Forms via `fetch` with `mode: 'no-cors'` (response is always opaque — success/failure cannot be confirmed from JS). Speeches still uses `mailto:` to `toastmaster@heinerud.se`.

Google Form: `https://docs.google.com/forms/d/e/1FAIpQLSeFQh8yBefVThrmpvkYMfhTAshiLLIvoavDe0rPwKrGijNP6Q/formResponse`

Entry IDs:
- `entry.1275700963` — Namn
- `entry.1019865349` — E-post
- `entry.1043987420` — Närvaro (`hela_helgen` | `vigsel_fest` | `bara_vigsel` | `kan_inte`)
- `entry.2048971199` — Matpreferenser
- `entry.1910555893` — Övernattning (`aras` | `ordnar_sjalva` | `ordnar_sjalva_vill_ha_frukost`)
- `entry.308973912`  — Övrigt

## Dynamic guest list (OSA form)

`addPerson()` creates a person card with namn, e-post, närvaro, and matpreferenser. Cards are indexed via `data-index` and collected by `collectPersoner()`. One Google Form response is submitted per person (in parallel). The first card is not removable.

## Images

Drop these files into the repo root to replace placeholders:
- `photo.jpg` — couple photo in the welcome section
- `herrgarden.jpg` — Herrgården in the information section
- `kvarnen.jpg` — Kvarnen in the information section
