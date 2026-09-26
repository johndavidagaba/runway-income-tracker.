# Runway — an income tracker for irregular earners

*A Ship & Found Bootcamp, Founder Track build.*

## The problem

Most budgeting tools assume a steady paycheck: money arrives on the 1st and 15th, expenses get planned around it. That model breaks down completely if you're paid irregularly — freelance work, side hustles, commission-based gigs. Some weeks are "feast," some are "famine," and there's no reliable schedule telling you which is coming next.

The result: you don't find out you're in trouble until you're already in trouble. Expenses don't pause to wait for the next payment to land.

## Who this is for

Freelancers, side-hustlers, and anyone whose income doesn't arrive on a predictable schedule but whose expenses still do.

## The core insight

The single most useful number an irregular earner needs isn't "how much did I make this month" — it's **"at my current rate of spending, how many days can I go before I run out?"** That's a number a generic budgeting app doesn't surface, because it assumes you already know when the next paycheck lands.

## MVP scope (Week 6)

Deliberately narrow. This is a V1, not the whole product.

**In scope:**
- Log an income entry (amount, source/client, date)
- Log an expense entry (amount, category, date)
- A single dashboard view: running balance + estimated "runway" (days left at current spend rate)

**Explicitly out of scope for V1 (parked for later):**
- Forecasting or predicting future income
- Budget limits / category caps
- Invoicing or client-facing features
- Multi-currency support
- Recurring expense automation

## Why these choices

- **One insight, not ten features.** The runway number is the entire point of the product. Everything else is noise until that works well and people actually want it.
- **No forecasting in V1.** Predicting irregular income is genuinely hard and easy to get wrong in a way that misleads people about money — better to under-promise here and get the basics right first.
- **Simple categories only.** Enough to be useful, not enough to become a second job to maintain.

## Tech stack

*(fill in once decided — e.g. HTML/CSS/JS + localStorage for a fast V1, or Next.js + a lightweight DB for persistence across devices)*

## Status

🟡 In progress — Week 6, MVP build phase.

## What's next

- Ship the three core flows above
- Get 2–3 real people (ideally other irregular earners) to try it and react to the runway number specifically
- Decide V2 priorities based on what they actually ask for, not what seems cool to build
