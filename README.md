# kb-4471-findings

Support ticket #4471 merged 412 date reports as one known issue. They are three problems:

| Problem | Reports |
|---|---|
| Shared parser reads dates month first | 374 |
| booking-v3 form hint says MM/DD/YYYY | 33 |
| Dates off by one day (likely time zone) | 5 |

- Issues: one per problem, each with its report count.
- `src/routes/kb/incidents/4471-split/+page.svx`: the kb page (signed `NataliaKurek`), with `src/lib/kb/CauseSplit.svelte`.
- `4471-split.rendered.html`: the page as the desk sees it (static render of the same data).
- `findings.json`: report ids per problem.
