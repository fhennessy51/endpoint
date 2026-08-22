# Endpoint (prototype)

A tool that matches an Irish student's goals to real career paths — degree, apprenticeship, PLC, teaching, etc. — instead of matching personality to a course.

## How it works

- `data/careers.json` holds every career as a list of **branches**. Each branch has:
  - `conditions`: which answers trigger this branch (e.g. `{"openToMoving": true}`)
  - `summary`, `facts`, `sources`, `verifiedDate`
- `index.html` is a small matcher: it asks a few questions, then shows every branch whose conditions match the answers.

## Running it locally

Browsers block a webpage from fetching a local JSON file directly, so don't just double-click `index.html`. From this folder, run:

```
python3 -m http.server
```

Then open `http://localhost:8000` in a browser.

## Currently has 11 careers

Electrician apprenticeship, actuary, investment banking, teacher, nurse, garda, hairdressing apprenticeship, software developer (degree route), software developer (apprenticeship route), business/marketing (unverified, flagged for review), chef apprenticeship, accounting technician apprenticeship — each hand-researched with real sources.

## Next steps (in order)

1. **See `PIPELINE.md`** for the full spec on how to research and add new careers consistently, including the draft-then-review safety flow.
2. **Show it to a real career guidance teacher**: 11 careers is enough to get an honest reaction — don't wait for a bigger dataset first.
3. **Grow the question set carefully once there's real feedback**: every new question multiplies the number of branches needed. Add one variable at a time.
4. **Only after real interest from a teacher**: consider more careers, a nicer UI beyond this prototype styling, and eventually hosting it somewhere real students can use it.

## A note on accuracy

Every fact in `careers.json` has `sources` and a `verifiedDate`. Points requirements especially change yearly — anything points-related should say "verify current points at cao.ie" rather than state a hard number as permanent fact.
