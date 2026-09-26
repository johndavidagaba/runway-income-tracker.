# PRD — Runway (irregular income tracker)

## 1. Problem

People with irregular income (freelancers, side-hustlers, commission earners) can't budget the way salaried people do. There's no predictable payday to plan around, so it's hard to know whether current spending is safe or dangerous until it's already too late.

## 2. Goal

Give the user one clear, always-visible number: how many days of runway they have left at their current rate of spending, based on their logged balance.

## 3. Target user

A single individual tracking their own irregular income and expenses. No teams, no multi-user accounts in V1.

## 4. Core user flow

1. User opens the app and sees their current balance and runway estimate.
2. User logs an income entry (amount, source, date) in a few taps.
3. User logs an expense entry (amount, category, date) in a few taps.
4. Balance and runway update immediately.

## 5. MVP feature list (V1 — build only this)

- **Add income entry**: amount (required), source/client (free text, required), date (defaults to today)
- **Add expense entry**: amount (required), category (select from a short fixed list: Rent, Food, Transport, Utilities, Other), date (defaults to today)
- **Dashboard view**:
  - Current balance (sum of all income minus all expenses)
  - Runway estimate: balance ÷ average daily spend over the last 14 days (or fewer if less history exists)
  - Simple list of recent entries (last 10), each editable/deletable
- **Data persistence**: entries must survive a page refresh / app restart

## 6. Explicitly out of scope for V1

- Income forecasting or prediction
- Budgets or spending caps per category
- Multi-currency support
- Recurring/automated entries
- Any multi-user, sharing, or export features
- Notifications or reminders

Do not build any of the above, even if it seems easy to add — flag it as an "open question for V2" instead of building it.

## 7. Non-negotiable technical rules

- No secrets or API keys hardcoded in the codebase. Use environment variables (`.env`), and ensure `.env` is in `.gitignore`.
- All amounts should be stored as integers in the smallest unit (e.g. kobo/cents) to avoid floating-point rounding errors — even though this is not a payments app, the habit is worth keeping from the start.
- Frontend input validation is required (e.g. amount must be a positive number, date required), but do not rely on frontend validation alone if there's any backend involved.
- If a database is used, no raw SQL from the agent — all queries go through an ORM.

## 8. Success criteria for V1

- A user can add both income and expense entries without errors.
- The runway number updates correctly and immediately after any entry is added, edited, or deleted.
- Data persists after closing and reopening the app.

## 9. Open questions (for the agent to flag, not resolve unilaterally)

- Should runway calculation use last 14 days of spend, last 30, or all-time average? (Default assumption above: 14 days — flag if this seems wrong.)
- Local-only storage vs. a backend database — pick based on whether cross-device sync matters for V1 (assume local-only unless told otherwise).

---

*Agent instructions: after reading this PRD, list your assumptions and any open questions before writing code. Do not invent features beyond section 6's scope.*
