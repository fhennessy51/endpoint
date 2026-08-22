# Career research pipeline

How to add a new career to `data/careers.json` — for a human doing it by hand, or Claude Code doing it with research/web tools.

## The rule that matters most

**Never write directly into `careers.json`.** New entries go into `data/drafts.json` first, marked `"reviewed": false`. A human (Fionn) checks each draft against real sources before promoting it into `careers.json`. The live matcher (`index.html`) only ever reads `careers.json`, so an unreviewed draft can never reach a real student by accident.

## Schema (matches the existing entries)

```json
{
  "id": "kebab-case-unique-id",
  "title": "Human-readable title",
  "requiresCollege": true or false,
  "reviewed": false,
  "branches": [
    {
      "conditions": {},
      "summary": "One line describing this branch",
      "facts": ["fact 1", "fact 2", "fact 3", "fact 4"],
      "sources": ["site.ie relevant page name", "another source"],
      "verifiedDate": "YYYY-MM"
    }
  ]
}
```

- `conditions` can be empty `{}` (branch always shows when the career matches), or key/value pairs like `{"openToMoving": true}` to create sub-paths within one career — see `investment-banking` and `teacher` in the existing file for examples of multi-branch careers.
- Every fact needs a real source behind it, and every source needs a real date. If a fact can't be sourced, don't include it — flag it as a gap instead.
- Points requirements, pay figures, and entry criteria change yearly. Always phrase these so they age honestly: "roughly 300 points, verify at cao.ie" beats a bare hardcoded number.

## Research checklist for one career

1. **What's the direct route?** (degree, apprenticeship, professional exams, direct entry — whichever applies)
2. **What does it actually require to get in?** (CAO points, Junior/Leaving Cert grades, age, other qualifications)
3. **What does it pay, realistically, starting out** — not just the ceiling?
4. **Is there a genuine no-college or lower-points fallback route?** This is often the most valuable fact in the entire entry — it's the thing personality-quiz tools miss.
5. **What's the real day-to-day like** — hours, structure, anything a 17-year-old would want to know before committing?

Use official/primary sources where they exist (SOLAS, CAO, Qualifax, the relevant professional body) over blogs or aggregator sites. Cross-check anything that smells stale.

## Reviewing a draft (Fionn's job, not automatable)

Before promoting a draft entry into `careers.json`:
- Open every source link. Does it actually say what the draft claims?
- Are the points/pay figures current, or from an old year?
- Does the "if points fall short" fallback actually exist, or was it invented to sound complete?
- Flip `"reviewed": false` to `true` only after checking all of the above, then move the object from `drafts.json` into `careers.json`.

## Current entries (11)

Electrician apprenticeship, actuary, investment banking, teacher, nurse, garda, hairdressing apprenticeship, software developer (degree route), software developer (apprenticeship route), business/marketing (**unverified, needs review**), chef apprenticeship, accounting technician apprenticeship.
