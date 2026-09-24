# Rider Partial Delivery: an AI-native PM case study

A customer ordered 5 items on cash-on-delivery. At the door they say "I only want 3."
This project designs how the rider completes that delivery, and gets it ready for development:
research, PRD, design system, clickable prototype and an AI-run audit.

Built as a product assignment for Zippee (quick-commerce logistics for D2C brands), July 2026.
By **Digvijay Singh Nayal**, Product Manager.

## What's here

| Path | What it is |
| --- | --- |
| `index.html` | Case study page: problem, the five-stage AI pipeline, key decisions, what the audit caught |
| `prototype/` | Clickable rider-app prototype (S1 to S7, Home, Success, RTO), exported from Claude Design |
| `assets/Digvijay_AI_PM_Case_Study.pdf` | The 5-page case study PDF |

## Run it locally

It's a static site, no build step:

```bash
npx serve .
```

Then open http://localhost:3000.

## Prototype scenarios

The prototype opens on the happy path. The chips above the phone switch to the PRD edge cases,
or you can set them in the URL:

| Scenario | URL |
| --- | --- |
| GPS drift (~400 m) | `prototype/?gps=drift_300m_1km` |
| Too far (~1.2 km), partial blocked | `prototype/?gps=beyond_1km` |
| Offline | `prototype/?offline=1` |
| UPI never paid (QR expires) | `prototype/?upi=never_pays&fast=1` |
| UPI under verification | `prototype/?upi=under_verification&fast=1` |

`fast=1` shortens the QR and OTP timers so the edge cases show up within seconds.
Demo OTP: `4821`.

React and ReactDOM are shipped in `prototype/vendor/` so the page doesn't depend on a
third-party CDN at runtime.
