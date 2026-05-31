# 🇮🇸 Iceland Trip — Andy & Alex

Single source of truth for our Iceland trip, **July 29 – August 6, 2026** (Southern Loop + Snæfellsnes).

## What's here

- `index.html` — the complete trip site. One self-contained file with:
  - **Interactive map** — click any day to follow that day's route; every pin links to Google Maps
  - **Day-by-day itinerary** with drive distances and where we sleep
  - **Base camps + options** — fixed lodging each night, flexible activity menu around each
  - **Scenic drive stops** — pull-offs between bases, with map links
  - **Lodging picks** by region (top picks + Alex's finds)
  - **Budget** estimate and **booking checklist**

No build step, no dependencies to install — Leaflet + map tiles load from CDN (so you need to be online to view the map).

## View locally

Open `index.html` in any browser.

## Deploy to GitHub Pages (free, permanent link)

1. Push this repo to GitHub.
2. Repo **Settings → Pages**.
3. **Source:** Deploy from a branch → **main** / **/ (root)** → **Save**.
4. ~1 min later it's live at `https://<username>.github.io/<repo-name>/`.
5. Share that URL with Alex.

## Editing the trip

Everything lives in the **`TRIP` object** near the top of the `<script>` block in `index.html` — days, bases, drive legs, lodging, budget, checklist. Edit the data there and the whole page (map + all sections) updates automatically. No other code changes needed.

To get coordinates for a new stop: right-click the spot in Google Maps → click the lat/lng to copy.

To mark a checklist item done: change its `false` to `true`.
