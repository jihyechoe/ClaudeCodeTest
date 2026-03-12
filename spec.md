# Migraine Diary — Product Spec

## Overview

Migraine Diary is a self-contained web application for tracking and analyzing migraine patterns. It runs entirely in the browser as a single HTML file with no external dependencies or backend services. All data is persisted locally via `localStorage`.

## Target User

Individuals who experience migraines and want to identify patterns in their triggers, symptoms, and severity over time.

## Features

### 1. Log Entry

A form to record a migraine episode with the following fields:

| Field | Type | Details |
|-------|------|---------|
| Date | date picker | Defaults to today |
| Time | time picker | Defaults to current time |
| Severity | range slider | 1–10 scale |
| Duration | number input | Hours, 0.5 step increments |
| Pain Location | multi-select pills | Forehead, Temples, Back of Head, Behind Eyes |
| Symptoms | multi-select pills | Nausea, Light Sensitivity, Sound Sensitivity, Aura, Vomiting |
| Triggers | multi-select pills | Stress, Sleep Deprivation, Dehydration, Food, Caffeine, Weather, Hormones |
| Medications | text input | Free-text (e.g., "Ibuprofen 400mg") |
| Notes | textarea | Free-text for additional details |

**Validation:** Date, time, and at least one pain location are required.

### 2. History

- Chronological list of all logged entries, newest first
- Each entry card displays: date, time, severity badge, duration, location/symptom/trigger tags, medications, and notes
- Edit button: loads the entry back into the Log Entry form for updating
- Delete button: removes the entry after confirmation prompt

### 3. Analytics

- **Stats grid:** This Month count, All-Time count, Average Severity, Most Common Trigger
- **Trigger Frequency:** Horizontal bar chart showing how often each trigger appears
- **Symptom Frequency:** Horizontal bar chart showing how often each symptom appears
- **Severity Over Time:** SVG bar chart of severity for the most recent 7 days with entries

All stats are computed on-the-fly from the entries array.

## Data Model

Entries are stored in `localStorage` under the key `migraine_diary_entries` as a JSON array:

```json
{
  "id": 1699564800000,
  "date": "2025-03-03",
  "time": "14:30",
  "severity": 7,
  "duration": 4,
  "locations": ["temples"],
  "symptoms": ["nausea"],
  "triggers": ["stress"],
  "medications": "Ibuprofen 400mg",
  "notes": "Free text notes"
}
```

- `id` is a unique timestamp generated via `Date.now()`
- Entries are sorted by date/time descending on load

## Architecture

- **Single file:** `migraine-diary.html` contains all HTML, CSS, and JavaScript
- **No external dependencies:** No frameworks, libraries, CDNs, or build tools
- **No backend:** All data stays in the browser's localStorage
- **Responsive design:** Single-column layout on mobile (< 600px breakpoint)

## Design

- **Theme:** Light mode with a light gray (#f5f5f5) background and white (#ffffff) cards
- **Accent color:** Blue (#1a6fa8) for labels, nav, stats, and charts
- **Severity accent:** Pink (#d63384) for severity badges and range values
- **Typography:** Segoe UI, sans-serif
- **Interactive elements:** Pill-style checkbox selectors, hover scale transitions, toast notifications

## How to Run

```bash
open migraine-diary.html
```

No install, no build step — just open the file in any modern browser.
