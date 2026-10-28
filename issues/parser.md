**Reports covered: 374** of the 412 merged into #4471.

Split out of #4471, which merged 412 date reports (2026-04-01 to 2026-10-04) as one known issue. The reports were grouped with the kb's own `causes.ts` logic plus `desk-notes.json`; the ids are in `findings.json`.

**Problem.** The shared parser reads every date month first. Tenants whose locale writes the day first get month and day flipped (for example 2 December shows as 12 February).

**Who.** All 11 tenants on file with a day-first locale, seen 2026-04-01 to 2026-10-04:
- `harbour.dental` (en-GB, booking-v2): 52
- `kettle.books` (nl-NL, booking-v2): 46
- `nine.lanterns` (pl-PL, booking-v2): 43
- `morrow.tax` (fr-FR, booking-v2): 40
- `long.table` (it-IT, booking-v2): 39
- `ridge.clinic` (da-DK, booking-v2): 36
- `stone.and.sons` (en-IE, booking-v2): 30
- `lantern.row` (cs-CZ, booking-v2): 27
- `alder.physio` (de-DE, booking-v3): 22
- `pale.harbour` (pt-PT, booking-v3): 20
- `copper.studio` (es-ES, booking-v3): 19

**Notes.**
- Most reports through app and email, plus form reports on booking-v2 (the form hint there is DD/MM/YYYY, so these are the parser, not the hint).
- This is the bug #4471 describes. The queued fix is for this one.
- `meta.intakeTag` is a browser guess and is wrong for 23 of the 379 reports that `causes.ts` places under parser, so it was not used.
- The 5 one-day-move reports are counted in #3 below, not here (379 − 5 = 374).

**Done when** a day-first tenant's date round-trips unchanged.
