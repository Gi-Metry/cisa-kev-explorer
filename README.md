# CISA KEV Explorer

A single-file web app that turns the [CISA Known Exploited Vulnerabilities catalogue](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) into a filterable, searchable view.

The KEV catalogue lists vulnerabilities with confirmed exploitation in the wild — the ones attackers are actually using, as opposed to the tens of thousands of CVEs published every year that mostly never see exploitation. It is one of the strongest prioritisation signals available in vulnerability management, and the reason I built this: I wanted a fast way to slice the catalogue by vendor, product, date added, and ransomware association, without spreadsheet gymnastics.

## What it does

- Loads the full KEV catalogue and renders it as a searchable, filterable table
- Filter by vendor, product, and free-text search across vulnerability names and descriptions
- Everything runs client-side in one HTML file — no backend, no build step, no dependencies

## Running it

Serve the folder with any static file server and open `index.html`:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

(Serving rather than double-clicking the file matters: browsers block `fetch` of local files from `file://` pages. If the automatic load is blocked, the app falls back to a manual file picker.)

## Data

The bundled `known_exploited_vulnerabilities.json` is a snapshot of the catalogue — **version 2026.06.12, 1,619 entries** — included so the app works instantly with no setup.

To use current data, download the latest catalogue JSON from [CISA's KEV page](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) and either replace the bundled file or load it through the app's file picker. The app works with any version of the catalogue file.

## How it was built

This app was vibe coded: built end to end with [Claude Code](https://claude.com/claude-code), with the AI writing the code and me directing the build: defining what a security practitioner needs from a KEV view, deciding the filters and layout, and shipping it as a dependency-free single file. I did not hand-write the code; the product decisions, the security use case, and the testing were mine.

## Author

Gina Metry
