# Tiramisu Tracker

A personal log of every tiramisu I eat, rated on a Tabelog-style 1–5 scale.

## How it works

All entries live in [`tiramisu.json`](tiramisu.json). The `index.html` page renders a Notion-style table from that data — deployable via GitHub Pages or any static host.

## Adding an entry

Add a new object to `tiramisu.json`:

```json
{
  "id": 4,
  "restaurant": "Via Carota",
  "address": "51 Grove St, New York, NY 10014",
  "address_url": "https://maps.google.com/?q=51+Grove+St,+New+York,+NY+10014",
  "rating": 4.4,
  "price": 17,
  "date": "2026-03-01",
  "notes": "Your tasting notes here."
}
```

Then push. That's it.

## Schema

| Field | Type | Description |
|---|---|---|
| `id` | number | Unique incrementing ID |
| `restaurant` | string | Restaurant or location name |
| `address` | string | Human-readable address |
| `address_url` | string | Google Maps link |
| `rating` | number | 1–5 (decimals allowed, Tabelog-style) |
| `price` | number | Price in USD |
| `date` | string | ISO date (`YYYY-MM-DD`) |
| `notes` | string | Tasting notes and rating justification |

## Rating scale (Tabelog-style)

| Score | Meaning | Badge color |
|---|---|---|
| 4.0+ | Elite | Green |
| 3.5–3.9 | Excellent | Blue |
| 3.0–3.4 | Good | Yellow |
| Below 3.0 | Average | Orange |

## Fetching from another site

If you want to display this data on another website, fetch the raw JSON from GitHub:

```js
const res = await fetch('https://raw.githubusercontent.com/Caleb-Cohen/Tiramisu/main/tiramisu.json');
const entries = await res.json();
```

## Local preview

```bash
# Any static server works
npx serve .
# or
python3 -m http.server
```

Then open `http://localhost:3000` (or `:8000` for Python).
