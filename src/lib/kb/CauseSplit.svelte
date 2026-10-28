<script lang="ts">
  import reports from '#lib/data/reports-4471.json';
  import notes from '#lib/data/desk-notes.json';
  import { groupByCause, uniqueById, type Report } from '#lib/kb/causes';
  import { tenantOf } from '#lib/kb/locales';

  let { ticket }: { ticket: number } = $props();

  const merged = $derived(uniqueById(reports as Report[]).filter((r) => r.mergedInto === ticket));
  const groups = $derived(groupByCause(merged, tenantOf));
  // The desk read these as a one-day move, not a month flip: a third problem, filed by tenant under `parser`.
  const dayMove = $derived(merged.filter((r) => notes.oneDayMove.includes(r.id)).length);
  const rows = $derived(
    groups.flatMap((g) =>
      g.cause === 'parser'
        ? [
            { name: 'parser', n: g.reports.length - dayMove },
            { name: 'one-day move', n: dayMove },
          ]
        : [{ name: g.cause, n: g.reports.length }],
    ),
  );
</script>

<table>
  <thead><tr><th>problem</th><th>reports</th></tr></thead>
  <tbody>
    {#each rows as r (r.name)}
      <tr><td><code>{r.name}</code></td><td>{r.n}</td></tr>
    {/each}
  </tbody>
  <tfoot><tr><td>total</td><td>{rows.reduce((s, r) => s + r.n, 0)}</td></tr></tfoot>
</table>
