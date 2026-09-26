# Agents.md — Runway (income tracker)

This is the general handbook for any AI agent working in this codebase. Read this before making changes. For the full product spec, see `docs/PRD.md`.

## Stack

- Plain HTML, CSS, and vanilla JavaScript. No frameworks, no build step, no bundler.
- Data persistence: browser `localStorage` only for V1. No backend, no database.
- No external libraries unless explicitly approved — this app should run by opening `index.html`, nothing to install.

## Folder structure

```
/
├── index.html          # single page app shell
├── styles.css          # all styling
├── app.js              # all application logic
├── agents.md           # AI handbook
├── docs/
│   ├── PRD.md
│   ├── project-journal.md
│   └── README.md
└── .gitignore
```

Do not create additional folders or files beyond this structure without flagging it as an open question first.

## Non-negotiables

- Never introduce a backend, server, or database. This is a client-only app for V1.
- Never add a build tool, package.json, or npm dependency without asking first.
- Never hardcode secrets or API keys anywhere in the codebase (not applicable yet, but stays true if this changes later).
- All monetary amounts must be handled as integers in the smallest currency unit internally (e.g. kobo), even though there's no payments processing yet — display formatting converts back to naira for the user.
- Frontend input validation is required on every form (amount must be a positive number, required fields must be filled) before any data is written to storage.

## Negotiables (can discuss/change with reasoning)

- Category list for expenses (currently: Rent, Food, Transport, Utilities, Other)
- The runway calculation window (currently: last 14 days of spend, or all available history if less than 14 days exist)
- Visual styling and layout, as long as it follows the color/typography token system already defined for this project

## Behavior rules

- Stick strictly to the scope in `docs/PRD.md`. Do not add features, screens, or settings that aren't listed there, even if they seem easy or useful.
- If the PRD is silent or ambiguous on something, do not guess. List it as an "open question" instead of making an assumption silently.
- At the end of every response, list any assumptions made and any open questions that came up.
- Keep functions small and single-purpose. Prefer clarity over cleverness — this codebase should be easy for a human to read and modify later.
- Comment non-obvious logic (especially the runway calculation), but don't over-comment obvious code.

## What "done" looks like for V1

- User can add an income entry and an expense entry.
- Dashboard shows current balance and runway estimate, and both update immediately after any change.
- Data survives a page refresh.
- No console errors on any of the three core actions.

---

*If you're an AI agent reading this: confirm you understand the scope boundary above before writing any code, and list your assumptions first.*
