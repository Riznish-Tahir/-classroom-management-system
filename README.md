# StarClass Pro

> A premium classroom management system for teachers — built as a single-file web app with no dependencies beyond Chart.js.

---

## Overview

StarClass Pro is a browser-based classroom star reward system styled after institutional school branding. Teachers can track daily student attendance and behaviour across six criteria, award stars, assign badges, take notes, and review history — all persisted locally in the browser.

**Live demo:** open `index.html` directly in any modern browser. No server, no build step, no install.

---

## Features

| Feature | Description |
|---|---|
| **Attendance tracking** | Six daily criteria per student: Attendance, Homework, Greeting, Performance, Class Work, Extra Credit |
| **Star awards** | Students scoring 5 or more out of 6 earn a star for the day |
| **Badge system** | Bronze (5+ stars), Silver (10+), Gold (20+) — automatically assigned |
| **Live scoring** | Checkbox scores update in real time with colour-coded pills |
| **Dashboard** | Bar chart overview, ranked leaderboard, recent activity log |
| **Student notes** | Per-student free-text notes, persisted across sessions |
| **Day history** | Full log of every save action with timestamps and student names |
| **Check all / Reset** | Bulk actions for speed during class |
| **Toast notifications** | Subtle feedback on every action |
| **Fully offline** | Zero network calls at runtime — works without internet |

---

## Getting Started

### 1. Clone or download

```bash
git clone https://github.com/your-username/starclass-pro.git
cd starclass-pro
```

Or simply download `index.html` — the entire application is one file.

### 2. Open in browser

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html   # Linux
```

### 3. Log in

| Field | Value |
|---|---|
| Username | `teacher` |
| Password | `1234` |

> **To change credentials:** edit the `doLogin()` function in the `<script>` block of `index.html`.

---

## Project Structure

```
starclass-pro/
└── index.html        # Entire application — HTML + CSS + JS in one file
```

All data is stored in the browser's `localStorage` under two keys:

| Key | Contents |
|---|---|
| `scWestData` | Per-student totals, daily stars, and notes |
| `scWestActivity` | Activity log (last 30 entries) |

---

## Student Roster

Edit the `STUDENTS` array near the top of the `<script>` block to change names:

```js
const STUDENTS = ["Aima", "Sameer", "Khadija", "Mudassir", "Amar", "Shayan", "Ayan", "Aizal"];
```

Any number of students is supported — the table and dashboard scale automatically.

---

## Star & Badge Thresholds

Edit these values in the `setBadge` / `updateBadge` logic:

| Badge | Default Threshold |
|---|---|
| 🥉 Bronze | 5 total stars |
| 🥈 Silver | 10 total stars |
| 🥇 Gold | 20 total stars |

A star is awarded when a student checks **5 or more** of the 6 daily criteria. Change this in `saveDay()`:

```js
if (n >= 5) { ... }   // ← adjust threshold here
```

---

## Data & Privacy

- All data stays **in the browser** — nothing is sent to any server.
- Clearing browser data or using a different browser will reset the app.
- To back up data, open DevTools → Application → Local Storage → copy the values of `scWestData` and `scWestActivity`.

---

## Dependencies

| Library | Version | Purpose | CDN |
|---|---|---|---|
| [Chart.js](https://www.chartjs.org/) | Latest | Bar chart on dashboard | `cdn.jsdelivr.net` |
| [Google Fonts](https://fonts.google.com/) | — | Cormorant Garamond + Inter | `fonts.googleapis.com` |

Both are loaded from CDN. The app requires an internet connection on first load to fetch fonts and Chart.js. Subsequent loads use the browser cache.

---

## Browser Support

| Browser | Support |
|---|---|
| Chrome / Edge | ✅ Full |
| Firefox | ✅ Full |
| Safari | ✅ Full |
| Mobile (iOS/Android) | ✅ Responsive layout |

---

## Customisation

### Change the colour palette

CSS custom properties are defined at the top of the `<style>` block:

```css
:root {
  --navy:       #0f254c;   /* primary brand colour */
  --navy2:      #0a1c3a;   /* darker navy for topbar */
  --gold:       #c9a84c;   /* accent — rules, highlights, active states */
  --gold2:      #e6c97a;   /* lighter gold on hover */
  --offwhite:   #f7f5f0;   /* page background */
}
```

### Change fonts

Replace the Google Fonts import URL and update the `font-family` values in `:root` and `body`.

### Add a new tab / panel

1. Add a `<button class="nav-tab">` to the `.nav` bar.
2. Add a `<div class="panel" id="panel-yourname">` to `#app`.
3. Handle it in `switchTab()`.

---

## Roadmap

- [ ] Export stars to CSV
- [ ] Multi-class support
- [ ] Teacher-configurable criteria labels
- [ ] Print-friendly report view
- [ ] Password change UI

---

## License

MIT — free to use, modify, and distribute.

---

*Built with care for teachers who inspire.*
