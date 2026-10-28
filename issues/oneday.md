**Reports covered: 5** of the 412 merged into #4471.

Split out of #4471, which merged 412 date reports (2026-04-01 to 2026-10-04) as one known issue. The reports were grouped with the kb's own `causes.ts` logic plus `desk-notes.json`; the ids are in `findings.json`.

**Problem.** These reports are not a month and day swap. The date is one day off. The reports describe one month only (June), an invite arriving before the booking was made, one meeting landing on Monday for a client in Toronto and Tuesday for a client in Lisbon, and Tuesday 6 October showing as Monday. That points to a time zone or midnight-boundary bug.

**Reports:** `R-41202`, `R-41209`, `R-41236`, `R-41344`, `R-41620` (the desk's `oneDayMove` list in `desk-notes.json`). Tenants: kettle.books ×1, alder.physio ×1, nine.lanterns ×1, pale.harbour ×1, lantern.row ×1.

**Notes.**
- By tenant these were filed under `parser`, so #4471 hid them.
- Confidence is lower than for the other two: five short reports. Needs an engineer to confirm the cause.

**Done when** the cause is confirmed or ruled out, and the reports are moved to a ticket of their own.
