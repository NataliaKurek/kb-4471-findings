**Reports covered: 33** of the 412 merged into #4471.

Split out of #4471, which merged 412 date reports (2026-04-01 to 2026-10-04) as one known issue. The reports were grouped with the kb's own `causes.ts` logic plus `desk-notes.json`; the ids are in `findings.json`.

**Problem.** booking-v3 prints `MM/DD/YYYY` under the date field. People at day-first tenants type month first because the form tells them to, and the form then reads it their way. A parser fix does not change this.

**Who.** Form reports only, 2026-04-17 to 2026-09-22:
- `alder.physio` (de-DE, booking-v3): 12
- `copper.studio` (es-ES, booking-v3): 11
- `pale.harbour` (pt-PT, booking-v3): 10

**Notes.**
- Intake tagged 15 of these as `parser` and 18 as `hint`; the tenant's form, not the tag, decides.
- Needs its own fix: the hint text (or the locale it is built for) on booking-v3.

**Done when** booking-v3 shows the tenant's own date order, or reads what the hint tells people to type.
