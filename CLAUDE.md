# Experiment Balboa

Balboa's training sandbox for writing and testing Pendo track events.
Live site: https://brianrochebalboa.github.io/experiment_balboa/
Owner: Brian Roche (Balboa). Anyone on the Balboa team may edit.

## How changes go live
- Every commit pushed to `main` republishes GitHub Pages in about a minute. No build step.
- Keep commits small and describe what changed for teammates.
- Pull before editing (`git pull`) since several people may push.

## Files
- `index.html`: the entire app (HTML, CSS, JS in one file). Keep it self-contained.
- `README.md`: human-facing usage notes.
- New pages: copy `index.html` to e.g. `campaigns.html`, then add a link in the side nav (`<aside class="sidenav">`) of every page.

## Pendo
- Balboa sandbox app ID: `036ed65f-4a54-4885-8ed5-5a8dcdfc2c90` (public install key, safe in page code).
- Never put a Pendo integration/API key in this repo. The repo and site are public.
- Section 1 in `index.html` is the Pendo loader. Do not edit it.
- `pendo.initialize()` runs anonymously on load; the sign-in form calls `pendo.identify()`.
  Visitor ID = `balboa-<name-slug>`. Accounts are fictional (see `ACCOUNTS`).
- Data goes only to Balboa's dedicated Pendo instance. Never point this site at a client or Pendo-owned subscription.

## Track event conventions
- Practice handlers live in section 3, "TRACK EVENT PRACTICE ZONE", at the bottom of `index.html`.
- Send events through `balboaTrack(name, props)`. It logs the payload and its byte size, then calls `pendo.track`.
- Event names: Title Case, stable. Properties: strings, numbers, booleans only. Keep total props well under 512 bytes.
- No PII and no long URLs in properties. The "Become a Balboa partner" card has a deliberately long URL for the size-limit exercise.
- "Read more" buttons sit inside two shadow DOM layers (`<eb-resource-card>` > `<eb-button>`). Read `data-*` from `event.currentTarget`.

## Brand
- Colors: Black #171717, Purple #6D2FAE, Green #098048, Blue #2073A5, Orange #D07628, Red #AA272C.
- Font: Avenir Next LT Pro, falling back to Nunito Sans.
- No references to real client brands or products. Use "Experiment Balboa" or "Balboa" for placeholder names.

## Testing a change
1. Open the live site, sign in, open DevTools Console.
2. `pendo.isReady()` should return `true`; `pendo.enableDebugging()` opens the debugger.
3. Trigger the change and confirm the `track` entry in the debugger Events tab.
