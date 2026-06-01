<div align="center">

# 🧭 ui-ergonomics

### A Claude Code skill that audits any screen against 18 usability dimensions — and scores it 0–100.

[![Skill](https://img.shields.io/badge/Claude%20Code-Skill-7c3aed)](https://docs.claude.com/en/docs/claude-code)
[![Rules](https://img.shields.io/badge/rules-128-0066cc)](reference/rules.json)
[![Dimensions](https://img.shields.io/badge/dimensions-18-16a34a)](#-the-18-dimensions)
[![License](https://img.shields.io/badge/license-MIT-black)](LICENSE)

_Point it at a view. Get back every rule it fails, a prioritized to-do list, and a score you can watch climb as you fix things._

</div>

---

> 📚 **Where the 128 rules come from:** they were collected and adapted from the **ErgoList usability
> checklist** developed at the **Federal University of Santa Catarina (UFSC), Brazil** — itself based
> on the classic **ergonomic criteria of Bastien & Scapin** — as published at
> [usabilidade.github.io](https://usabilidade.github.io). Translated to English and made
> source-neutral here so they're reusable anywhere. They're a strong baseline, not gospel: every rule
> is editable in [`reference/rules.json`](reference/rules.json).

---

## ✨ What it does

`ui-ergonomics` reviews a screen or component against **18 usability & ergonomic dimensions**
(~128 concrete rules) and exports a clean markdown report:

- ✅ **Pass / ❌ Fail / ➖ N-A** verdict for every rule, with your notes
- 📊 a **0–100 global score** plus a per-dimension breakdown
- 📋 a **prioritized next-steps list** (worst dimensions first)
- 🔁 a **coverage metric** so a half-finished audit can never masquerade as a good one

Re-run it after each round of fixes and the **score is your progress bar**.

---

## 🚀 Quick start

**1. Install** — drop the skill into your Claude Code skills folder:

```bash
# global (available in every project)
git clone git@github.com:jackesdavid/skills-ui-ergonomics.git ~/.claude/skills/ui-ergonomics

# …or per-project
git clone git@github.com:jackesdavid/skills-ui-ergonomics.git .claude/skills/ui-ergonomics
```

**2. Audit** — just ask Claude Code:

> _"Run a usability audit on my LoginScreen."_

Claude reads the component, judges all 128 rules, writes an assessment, scores it, and hands you the report.

**3. Score manually** (optional) — the engine is a dependency-free Node script:

```bash
# generate a blank assessment skeleton for a view
node scripts/score.mjs --template LoginScreen > assessments/LoginScreen.json

# …fill in pass / fail / na for each rule, then score it
node scripts/score.mjs assessments/LoginScreen.json --out assessments/LoginScreen.report.md
```

---

## 📊 Example report

Here's a real run against a typical mobile **LoginScreen** — see [`examples/`](examples/) for the full output.

> # UI Ergonomics Report — LoginScreen
>
> ## Global Score: 64/100 🟡 Acceptable
>
> ```
> ██████░░░░  64%
> ```
>
> - ✅ Achieved: **38** ❌ Not achieved: **21** ➖ Not applicable: **69** · 📊 Coverage: **100%**

**Score by dimension** (excerpt):

| Dimension | Score | Bar | ✅ | ❌ | ➖ |
|---|---:|---|---:|---:|---:|
| Prompting | 17% | `██░░░░░░░░` | 1 | 5 | 11 |
| Grouping by Format | 56% | `██████░░░░` | 5 | 4 | 8 |
| Feedback | 50% | `█████░░░░░` | 3 | 3 | 6 |
| Legibility | 100% | `██████████` | 7 | 0 | 20 |
| User Control | 0% | `░░░░░░░░░░` | 0 | 1 | 3 |
| Error Messages | 0% | `░░░░░░░░░░` | 0 | 1 | 0 |

**Rules not achieved** (excerpt) — every failure is explained:

```
### Prompting
- ❌ PRE-02 — Do all fields and data displays have identifying labels?
  ↳ Fields use placeholders only; label disappears on typing — no persistent label
- ❌ PRE-13 — Does the user find the information needed for their actions readily available?
  ↳ Missing essential guidance: no 'forgot password', no 'create account'

### Error Messages
- ❌ MSG-01 — Are error messages clear and precise, indicating the cause and how to correct it?
  ↳ Failure message is generic — does not indicate cause nor how to fix
```

**Next steps** — sorted so you fix the biggest gaps first:

```
1. User Control     (0%)  — resolve 1 rule(s)
2. Error Messages   (0%)  — resolve 1 rule(s)
3. Prompting        (17%) — resolve 5 rule(s)
4. Conciseness      (40%) — resolve 3 rule(s)
```

👉 Full report: [`examples/LoginScreen.report.md`](examples/LoginScreen.report.md)

---

## 🧮 How scoring works

| Metric | Formula |
|---|---|
| **Per dimension** | `pass / (total − na) × 100` |
| **Global score** | `pass / (all applicable rules) × 100`, rounded 0–100 |
| **Coverage** | `% of rules explicitly evaluated` (pending rules count against you) |

`na` (not applicable) rules are excluded from the denominator, so a login screen isn't punished
for lacking tables or charts — **as long as you mark them honestly**.

**Maturity levels:** 🟢 90+ Excellent · 🟢 75+ Good · 🟡 60+ Acceptable · 🟠 40+ Weak · 🔴 &lt;40 Critical

---

## 🗂 The 18 dimensions

| | | | |
|---|---|---|---|
| **Prompting** | **Grouping by Location** | **Grouping by Format** | **Feedback** |
| **Legibility** | **Conciseness** | **Minimal Actions** | **Information Density** |
| **Explicit User Actions** | **User Control** | **Flexibility** | **User Experience** |
| **Error Protection** | **Error Messages** | **Error Correction** | **Consistency** |
| **Significance of Codes** | **Compatibility** | | |

Every rule lives in a single file: [`reference/rules.json`](reference/rules.json).

---

## 🛠 Make it yours

The rules are **adapted from a Brazilian university usability study** — a classic, well-tested set
of ergonomic evaluation criteria. They're a strong, neutral baseline, **not gospel**.

Everything is one plain JSON file, so:

- ✏️ **Edit** any rule's wording to fit your product's language
- ➕ **Add** rules for your design system, brand, or accessibility bar
- ➖ **Remove** rules that don't apply to your platform
- 🆔 Keep the `id`s stable so historical reports stay comparable

The scorer reads whatever is in `rules.json` — no code changes needed to reshape the checklist.

---

## 📁 Repo layout

```
ui-ergonomics/
├── SKILL.md              # the Claude Code skill definition + workflow
├── reference/rules.json  # all 18 dimensions & ~128 rules (edit me!)
├── scripts/score.mjs     # zero-dependency scorer + report generator
└── examples/             # a sample LoginScreen audit + report
```

---

## 📜 License

MIT — free to use, change, and share.

<div align="center">

Made with care for anyone who wants their UIs to feel *right*. ⭐ it if it helped!

</div>
