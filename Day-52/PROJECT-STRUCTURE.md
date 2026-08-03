# PROJECT-STRUCTURE.md — TRIAGE//44

## Final Folder Structure

```
triage-44/
├── README.md
├── .gitignore
├── index.html
├── docs/
│   ├── PRD.md
│   ├── IMPLEMENTATION-BLUEPRINT.md
│   ├── PITCH-DECK.md
│   ├── ARCHITECTURE.md
│   ├── SCHEMA.md
│   ├── API.md
│   ├── UI-WIREFRAMES.md
│   ├── PROJECT-STRUCTURE.md
│   └── daily-log/
│       └── day52.md
├── src/
│   ├── css/
│   │   ├── theme.css
│   │   └── layout.css
│   ├── js/
│   │   ├── app.js
│   │   ├── scenarioEngine.js
│   │   ├── scoringEngine.js
│   │   ├── progressStore.js
│   │   └── themeManager.js
│   └── data/
│       └── scenarios.json
├── assets/
│   ├── fonts/           (fallback local fonts, optional)
│   └── icons/           (inline SVG source files, if kept separate from code)
└── tests/
    └── smoke/
        └── scenario-load.test.js
```

## Purpose of Each Folder/File

| Path | Purpose |
|---|---|
| `index.html` | Single entry point — the entire app shell (Start/Scenario/Feedback/Summary sections toggled via JS) |
| `docs/` | All planning and design documentation — the single source of truth referenced throughout this build |
| `docs/daily-log/` | Per-day build logs (day52.md, day53.md, …) for the ABTalks challenge trail |
| `src/css/theme.css` | CSS variables for dark/light themes (colors, only) |
| `src/css/layout.css` | Structural/responsive layout rules, independent of theme |
| `src/js/app.js` | Controller — initializes modules, wires DOM events |
| `src/js/scenarioEngine.js` | Scenario loading/navigation logic (API.md §scenarioEngine) |
| `src/js/scoringEngine.js` | Answer-checking and accuracy logic (API.md §scoringEngine) |
| `src/js/progressStore.js` | localStorage read/write interface (API.md §progressStore) |
| `src/js/themeManager.js` | Theme get/set logic (API.md §themeManager) |
| `src/data/scenarios.json` | The 44 authored scenarios (SCHEMA.md) |
| `assets/` | Static, non-code assets — kept separate from `src/` so design assets don't clutter logic folders |
| `tests/smoke/` | Lightweight jsdom/Node smoke tests — validates scenario count/schema and basic app init, per standard practice |

## Why This Structure

- **`src/js` split by module, one file per responsibility** — mirrors the module boundaries defined in API.md exactly, so Day 53 implementation maps 1:1 from doc to file with zero translation needed
- **`docs/` at the repo root, not buried** — keeps the source-of-truth documents visible and versioned alongside the code they describe
- **No `backend/` folder** — intentionally absent, reflecting the confirmed client-side-only architecture; if a backend is ever added later (ARCHITECTURE.md §10), it would live as a sibling `server/` folder without disrupting this structure
- **`tests/` isolated from `src/`** — keeps shippable app code separate from dev-only tooling
- **Single `index.html` at root** — required for GitHub Pages to serve the site directly from `main` with zero configuration

## Scalability

Adding new scenarios only touches `src/data/scenarios.json`. Adding a new screen/state only touches `app.js` + one CSS/JS module — no restructuring needed for anything currently on the roadmap.
