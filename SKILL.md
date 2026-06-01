---
name: ui-ergonomics
description: "Use when auditing whether a view/screen is correctly built against usability & ergonomic dimensions. Checks a UI against 18 usability dimensions — prompting, grouping by location/format, feedback, legibility, conciseness, minimal actions, information density, explicit user actions, user control, flexibility, error protection/messages/correction, consistency, significance of codes, compatibility. Produces a markdown report of all unmet rules, a prioritized next-steps list, and a 0-100 score to track implementation progress over time. Triggers: 'check this view', 'usability audit', 'ergonomics review', 'is this screen correct'."
user-invocable: true
argument-hint: "[view-name or path to component]"
allowed-tools:
  - Bash(node *)
  - Read
  - Glob
  - Grep
---

# UI Ergonomics — Usability Dimension Auditor

Audits a view against **18 usability dimensions**. It outputs a markdown report listing every rule
**not achieved**, a prioritized **next-steps** list, and a **0–100 score** so progress can be
tracked across re-runs. Source-neutral and in English — reusable across any company or product.

## The dimensions

All rules live in `reference/rules.json` — the single source of truth. 18 dimensions, ~128 rules:

| # | Dimension | # | Dimension |
|---|---|---|---|
| PRE | Prompting | DEN | Information Density |
| AGL | Grouping by Location | AEX | Explicit User Actions |
| AGF | Grouping by Format | CTL | User Control |
| FBK | Feedback | FLE | Flexibility |
| LEG | Legibility | EXP | User Experience |
| CON | Conciseness | PRO | Error Protection |
| AMI | Minimal Actions | MSG | Error Messages |
| CST | Consistency | COR | Error Correction |
| SIG | Significance of Codes | CMP | Compatibility |

## Workflow

1. **Identify the view.** Take the view name/path from the argument (e.g. a screen or component
   file). Read the component file(s) — markup, styles, copy, states, and any relevant child
   components.

2. **Load the rules.** Read `reference/rules.json`. For each of the ~128 rules, judge the view as:
   - `pass` — the rule is satisfied.
   - `fail` — the rule is violated / not implemented.
   - `na` — the rule does not apply to this view (e.g. no tables on a login screen → table rules
     are `na`). `na` rules are excluded from the denominator, so marking honestly matters.
   Be conservative: if you cannot confirm a rule is met from the code, mark `fail`, not `pass`.

3. **Write the assessment JSON.** Save to `assessments/<view>.json` with this shape:
   ```json
   {
     "view": "LoginScreen",
     "platform": "<app or platform>",
     "assessedAt": "2026-05-31",
     "results": {
       "PRE-01": { "status": "pass" },
       "PRE-02": { "status": "fail", "note": "Email field has no identifying label" },
       "PRE-08": { "status": "na" }
     }
   }
   ```
   Tip: generate a blank skeleton (all rules pre-listed) with
   `node scripts/score.mjs --template LoginScreen > assessments/LoginScreen.json`, then edit each
   status. A rule omitted from `results` counts as **pending** (not-yet-achieved) and is reported
   under coverage — so prefer filling every rule.

4. **Score & generate the report.**
   ```bash
   node scripts/score.mjs assessments/LoginScreen.json --out assessments/LoginScreen.report.md
   ```
   The script prints a console summary and writes the full markdown report.

5. **Report back** the Global Score, the worst dimensions, and the top next steps. Point the
   user to the generated `.report.md`.

## Scoring

- **Per dimension:** `score = pass / (total − na) × 100`.
- **Global:** `pass / (total applicable rules across all dimensions) × 100`, rounded to 0–100.
- **Coverage:** % of rules explicitly evaluated (not left pending) — shown so a high score on a
  half-filled assessment is never mistaken for real quality.
- **Levels:** 🟢 90+ Excellent · 🟢 75+ Good · 🟡 60+ Acceptable · 🟠 40+ Weak · 🔴 <40 Critical.

To **track progress**, re-run after fixes and compare the Global Score. Keep each view's
`assessments/<view>.json` in the repo as the running record; the diff between report runs is the
implementation progress.

## Report contents

The generated `.report.md` always includes:
- Global Score with a progress bar + maturity level.
- A per-dimension table (score, bar, pass/fail/pending/na counts).
- **Rules Not Achieved** — every failed rule, grouped by dimension, with your notes.
- **Next Steps** — dimensions ordered worst-first with the count of rules to fix.
- **Rules Not Yet Evaluated** — coverage gaps, if any.

## Notes

- Use this skill to verify a view after it's built, or to baseline an existing screen before a
  redesign. It checks and scores UI; it does not produce UI.
- Rules and reports are in English so the skill is portable across companies and products.
