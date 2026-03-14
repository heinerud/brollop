# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the site

Just open `index.html` directly in a browser — no server, no build step.

## Architecture

Pure HTML + CSS + vanilla JS. Single page, no dependencies, no backend.

- `index.html` — entire site: nav, hero, information, OSA, tal & framträdanden
- `style.css` — all styles

## Changing the color palette

All colors are CSS custom properties in the `:root` block at the top of `style.css`. Change them there and everything updates automatically.

## Form submission

Both forms (OSA and tal & framträdanden) collect input, build a pre-filled `mailto:` URL, and open the user's default email client. The recipient address is set in the `RECIPIENT` constant at the top of the `<script>` block in `index.html`.

## Dynamic guest list (OSA form)

The OSA form has a JS-driven guest list. `addPerson()` creates a card with a name field and närvaro radio buttons. Person cards are indexed via `data-index` and collected by `collectPersoner()` before the mailto is built. The first card is not removable.
