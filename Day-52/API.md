# API.md — TRIAGE//44

**Architecture note:** TRIAGE//44 v1 has **no backend and no network API** (confirmed client-side-only). What follows documents the **internal application interface** — the function-level contracts between modules — using the same rigor a networked API doc would have, so Day 53 implementation has zero ambiguity. This substitutes for REST endpoint documentation in this project.

---

## Module: `scenarioEngine.js`

### `loadScenarios()`
- **Purpose:** Load and validate the 44 scenarios from `scenarios.json`
- **Input:** none
- **Output:** `Promise<Scenario[]>`
- **Validation:** throws if count ≠ 44, or if any entry is missing a required field (see SCHEMA.md)
- **Errors:** `ScenarioLoadError` — caught by `app.js`, triggers the error state in ARCHITECTURE.md §9
- **Business rule:** must run once on app init before any UI is interactive

### `getCurrentScenario(index)`
- **Purpose:** Return the scenario object for the given index
- **Input:** `index: number` (0–43)
- **Output:** `Scenario`
- **Errors:** returns `null` if index out of range (triggers Summary screen instead)

### `advance(index)`
- **Purpose:** Compute the next index
- **Input:** `index: number`
- **Output:** `number` (index + 1, capped at 44 meaning "complete")

---

## Module: `scoringEngine.js`

### `submitAnswer(scenario, userAnswer)`
- **Purpose:** Core classification-check function
- **Input:**
  - `scenario: Scenario`
  - `userAnswer: "malicious" | "benign" | "needs_investigation"`
- **Output:**
  ```
  {
    isCorrect: boolean,
    correctAnswer: string,
    explanation: string
  }
  ```
- **Validation rules:** `userAnswer` must be one of the 3 enum values — reject/ignore otherwise (defensive check; UI should never allow an invalid value to be sent)
- **Business rule:** exact match only, no partial credit

### `calculateAccuracy(score, totalAnswered)`
- **Purpose:** Derive accuracy percentage for live display and summary screen
- **Input:** `score: number`, `totalAnswered: number`
- **Output:** `number` (0–100, rounded to nearest whole number)
- **Edge case:** returns `0` when `totalAnswered === 0` (avoid divide-by-zero)

---

## Module: `progressStore.js`

### `getProgress()`
- **Purpose:** Read current progress from localStorage
- **Output:** `Progress` object (see SCHEMA.md) or a fresh default object if none exists
- **Errors:** if localStorage is blocked (private browsing edge cases), returns an in-memory default and logs a warning — app continues without persistence (ARCHITECTURE.md §9)

### `saveProgress(progress)`
- **Purpose:** Persist progress after every answer
- **Input:** `Progress` object
- **Output:** `boolean` (success/failure)
- **Business rule:** called immediately after every `submitAnswer()` — no batching, no debounce, since writes are small and infrequent (max 44 per session)

### `resetProgress()`
- **Purpose:** Clear all progress (user-initiated "Reset" action)
- **Input:** none
- **Output:** none
- **Business rule:** requires a confirmation step in the UI (destructive action) — see UI-WIREFRAMES.md

---

## Module: `themeManager.js`

### `getTheme()`
- **Output:** `"dark" | "light"` — reads from `triage44_settings`, defaults to `"dark"` if unset

### `setTheme(theme)`
- **Input:** `theme: "dark" | "light"`
- **Output:** none
- **Side effect:** applies theme class to `<body>`, persists via `progressStore`-style localStorage write

---

## Error Catalog (applies across modules)

| Error | Trigger | UI Response |
|---|---|---|
| `ScenarioLoadError` | `scenarios.json` fails to fetch/parse or fails count validation | Full-page error state with Retry |
| `StorageUnavailableError` | localStorage blocked | Non-blocking warning banner, app continues in memory-only mode |
| `InvalidAnswerError` | (defensive only) `userAnswer` not one of the 3 enums | Ignored client-side; should be unreachable via normal UI |

## Status Codes

Not applicable — no HTTP layer in v1. If a backend is added in a future version (per ARCHITECTURE.md §10 scalability note), this document should be extended with standard REST conventions (200/400/404/500) at that time, not before.
