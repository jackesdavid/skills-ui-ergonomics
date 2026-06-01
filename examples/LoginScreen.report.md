# UI Ergonomics Report — LoginScreen

> Framework: UI Ergonomics — Usability Dimensions Checklist v1.0
> Platform: React Native (Expo) · Assessed: 2026-05-31

## Global Score: 64/100 🟡 Acceptable

```
██████░░░░  64%
```

- ✅ Achieved: **38**
- ❌ Not achieved: **21**
- ⏳ Pending (not evaluated): **0**
- ➖ Not applicable: **69**
- 📊 Assessment coverage: **100%** (128/128 rules evaluated)

## Score by Dimension

| Dimension | Score | Bar | ✅ | ❌ | ⏳ | ➖ |
|---|---:|---|---:|---:|---:|---:|
| Prompting | 17% | `██░░░░░░░░` | 1 | 5 | 0 | 11 |
| Grouping by Location | 100% | `██████████` | 5 | 0 | 0 | 6 |
| Grouping by Format | 56% | `██████░░░░` | 5 | 4 | 0 | 8 |
| Feedback | 50% | `█████░░░░░` | 3 | 3 | 0 | 6 |
| Legibility | 100% | `██████████` | 7 | 0 | 0 | 20 |
| Conciseness | 40% | `████░░░░░░` | 2 | 3 | 0 | 9 |
| Minimal Actions | 50% | `█████░░░░░` | 2 | 2 | 0 | 1 |
| Information Density | 100% | `██████████` | 5 | 0 | 0 | 4 |
| Explicit User Actions | 100% | `██████████` | 3 | 0 | 0 | 1 |
| User Control | 0% | `░░░░░░░░░░` | 0 | 1 | 0 | 3 |
| Flexibility | 0% | `░░░░░░░░░░` | 0 | 1 | 0 | 0 |
| User Experience | 0% | `░░░░░░░░░░` | 0 | 1 | 0 | 0 |
| Error Protection | 100% | `██████████` | 1 | 0 | 0 | 0 |
| Error Messages | 0% | `░░░░░░░░░░` | 0 | 1 | 0 | 0 |
| Error Correction | 100% | `██████████` | 1 | 0 | 0 | 0 |
| Consistency | 100% | `██████████` | 1 | 0 | 0 | 0 |
| Significance of Codes | 100% | `██████████` | 1 | 0 | 0 | 0 |
| Compatibility | 100% | `██████████` | 1 | 0 | 0 | 0 |

## Rules Not Achieved

### Prompting

- ❌ **PRE-02** — Do all fields and data displays have identifying labels?  
  ↳ _Fields use placeholders only ('Email'/'Password'); label disappears on typing — no persistent label_
- ❌ **PRE-05** — Do field labels contain a specific element (e.g. ':') as an invitation for data entry?  
  ↳ _No fixed labels, hence no ':' or entry-invitation element_
- ❌ **PRE-13** — Does the user find the information needed for their actions readily available?  
  ↳ _Missing essential guidance: no 'forgot password', no 'create account' — user has no recovery route_
- ❌ **PRE-14** — In error message boxes, is a 'HELP' command button always present?  
  ↳ _Error is inline text; no Help button/affordance_
- ❌ **PRE-17** — When errors occur, can the user access all the information needed to diagnose and solve the problem?  
  ↳ _Generic failure message gives no diagnosis nor path to a solution_
### Grouping by Format

- ❌ **AGF-04** — Are labels visually different from the data they are associated with?  
  ↳ _No label separate from the data; placeholder shares the same field/style as the value_
- ❌ **AGF-09** — Are items selected for change, update or activation highlighted from the others?  
  ↳ _Inputs have no styled focus state (active field not highlighted)_
- ❌ **AGF-11** — Are required fields differentiated from optional fields in a visually clear way?  
  ↳ _Both fields are required but there is no visual indication of requiredness_
- ❌ **AGF-17** — When presenting options that are currently unavailable, does the system show them in a visually differentiated way?  
  ↳ _Button gets disabled during loading but with no visual change (opacity/color) — unavailable state not differentiated_
### Feedback

- ❌ **FBK-02** — When the system becomes unavailable due to long processing, is the user warned of this state and of the duration of the unavailability?  
  ↳ _During the request, no state/duration of unavailability is shown beyond the spinner_
- ❌ **FBK-06** — Does the system give the user information about the duration of lengthy processing?  
  ↳ _No duration indication for the login network call_
- ❌ **FBK-09** — Does the system set the action focus to newly created or newly opened objects?  
  ↳ _No autoFocus: focus does not land on the first field when the screen opens_
### Conciseness

- ❌ **CON-01** — Does the system offer default values to speed up data entry?  
  ↳ _No default value (e.g. remembered email) to speed up entry_
- ❌ **CON-10** — When entering alphanumeric data, does the system treat uppercase and lowercase letters as equivalent?  
  ↳ _Email is not normalized (lower-cased) on the client; upper/lower not treated as equivalent_
- ❌ **CON-14** — Is the user allowed to reuse values defined for previous entries, and even to modify them?  
  ↳ _No 'remember email' / reuse of previous entries_
### Minimal Actions

- ❌ **AMI-01** — In data-entry forms, does the system position the cursor at the start of the first input field?  
  ↳ _Cursor is not auto-positioned in the first field (no autoFocus)_
- ❌ **AMI-03** — Does the user have a simple and quick way (e.g. the TAB key) to navigate between the fields of a form?  
  ↳ _Return key 'next' on email does not move focus to password (no chained ref)_
### User Control

- ❌ **CTL-04** — During periods when input devices are blocked, does the system provide an option to interrupt the process that caused the block?  
  ↳ _During loading there is no option to cancel/interrupt the in-flight login request_
### Flexibility

- ❌ **FLE-01** — Does the system let the user personalize actions to account for their needs, habits or preferences?  
  ↳ _No personalization (remember-me, biometrics, preferences)_
### User Experience

- ❌ **EXP-01** — Does the system offer opportunities for success to both novice and experienced users (e.g. shortcuts, assistance)?  
  ↳ _No affordances for experienced users (biometrics/saved login) nor assistance for novices beyond the basics_
### Error Messages

- ❌ **MSG-01** — Are error messages clear and precise, indicating the cause of the error and how to correct it?  
  ↳ _Failure message is generic — does not indicate cause nor how to fix_

## Next Steps

1. **User Control** (0%) — resolve 1 rule(s) to raise this dimension's score.
2. **Flexibility** (0%) — resolve 1 rule(s) to raise this dimension's score.
3. **User Experience** (0%) — resolve 1 rule(s) to raise this dimension's score.
4. **Error Messages** (0%) — resolve 1 rule(s) to raise this dimension's score.
5. **Prompting** (17%) — resolve 5 rule(s) to raise this dimension's score.
6. **Conciseness** (40%) — resolve 3 rule(s) to raise this dimension's score.
7. **Feedback** (50%) — resolve 3 rule(s) to raise this dimension's score.
8. **Minimal Actions** (50%) — resolve 2 rule(s) to raise this dimension's score.
9. **Grouping by Format** (56%) — resolve 4 rule(s) to raise this dimension's score.

---
_To track progress, re-run the assessment after fixes and compare the Global Score (64/100)._
