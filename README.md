# 🇮🇸 Iceland Trip — Andy & Alex

Single source of truth for our Iceland trip, **July 29 – August 6, 2026** (Southern Loop + Snæfellsnes).

🔗 **Live site:** **https://andyfeng13.github.io/iceland-2026/**

## What's here

- `index.html` — the complete trip site. One self-contained file with:
  - **Interactive map** (MapLibre GL) beside a tabbed trip panel — click a day or stop to fly there; click a map pin to jump to it in the list (two-way sync). Every pin links out to Google Maps.
  - **Day-by-day itinerary** with drive distances and where we sleep
  - **Base camps + options** — fixed lodging each night, flexible activity menu around each
  - **Scenic drive stops** — pull-offs between bases, with map links
  - **Lodging picks** by region (top picks + Alex's finds)
  - **Budget** estimate
  - **Booking checklist** you can tap to check off — saved automatically in your browser (per device; see below)
  - **Weather & packing** — what to expect for the dates, plus a tappable packing checklist (also saved per device)

No build step, no dependencies to install — the map uses **MapLibre GL** with vector tiles from a CDN (so you need to be online to see the map; all the trip info still works offline).

## View locally

Open `index.html` in any browser.

## Hosting

The site is **live on GitHub Pages** at <https://andyfeng13.github.io/iceland-2026/>, served from the `main` branch (root folder), HTTPS enforced.

**Every push to `main` redeploys automatically** in ~1 minute — no extra steps. To update the trip, edit `index.html`, commit, and push.

## Editing the trip

Everything lives in the **`TRIP` object** near the top of the `<script>` block in `index.html` — days, bases, drive legs, lodging, budget, checklist. Edit the data there and the whole page (map, pins, routes, and every tab) updates automatically. No other code changes needed.

The shapes (also summarized in a comment right above the object):

| Key | Shape |
| --- | --- |
| `days[]` | `{ id, label, date, title, drive, sleep, stops[] }` |
| `days[].stops[]` | `{ name, type: 'base'\|'sight', star: true/false, lat, lng, desc }` |
| `bases[]` | `{ title, nights, items: [ [name, star, desc] ] }` |
| `legs[]` (drive stops) | `{ title, note, stops: [ [name, desc, lat, lng] ] }` |
| `lodging[]` | `{ region, picks: [ [name, rating, price, desc, top, url?] ], more?: [ [label, url] ] }` |
| `budget[]` | `[ item, estimate, note ]`  (plus `budgetTotal`) |
| `checklist[]` | `[ text, defaultChecked ]` |
| `booked[]` | `[ label, sharedTotalCost, paidBy ]` — running "booked so far" tally (split two ways; who paid) |
| `weather` | `{ summary, facts: [ [label, value] ], rule, skip: [ ... ] }` |
| `packing[]` | `{ cat, items: [ ... ] }` |

- **Coordinates:** right-click a spot in Google Maps → click the lat/lng to copy. Map pins read `lat`/`lng`; note the drive-leg tuples are ordered `name, desc, lat, lng`.
- **Checklist:** the `defaultChecked` value is only the *starting* state. On the live site you tick items off by tapping them, saved in the browser's `localStorage` — **per device and per browser** (your phone and laptop don't sync), and separately for the local file vs. the deployed site. Editing an item's wording resets that one item's saved check.
