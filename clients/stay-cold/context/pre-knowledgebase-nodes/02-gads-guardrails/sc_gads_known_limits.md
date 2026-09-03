# Stay Cold Google Ads — known limits of this knowledge (do not overclaim)

### Margin and returns are unknown — no profitability threshold exists

[Stay Cold · Google Ads · known limit · as of 2026-07-03]
All ROAS figures in this knowledge pack are gross platform revenue
(Mable-attributed purchases) divided by ad cost. Product margin (DB1) and
return rates are not in the account. Non-brand clean ROAS was 2.40 (90-day
view as of 2026-07-03) — whether that is profitable is undecidable without
margin data. Any agent asked for a break-even or target ROAS must state that
this number requires margin input from Stay Cold and does not exist in this
knowledge yet.

### PMax internals are a partial black box

[Stay Cold · Google Ads · known limit · as of 2026-07-03]
Performance-Max campaigns expose no search terms and no impression-share
metrics in this account's data. Saturation diagnosis via budget-lost
impression share works only for Search and standard Shopping; for PMax the
proxy is the marginal clean ROAS of the last budget step. An asset-group
level deep-dive was prepared (daily asset-group data pulled to 2026-07-03)
but has not been analyzed yet.

### Attribution is an approximation, not causal proof

[Stay Cold · Google Ads · known limit · as of 2026-07-03]
All effect numbers are trend-corrected pre/post comparisons (DiD, 28 days),
not experiments. Only 8 of 467 evaluated clusters meet the highest confidence
bar (|effect| ≥ 30 %, ≤ 3 parallel changes, no counting-regime break in the
window). During sale windows with 100+ parallel changes, individual
attribution is impossible and the analysis says "unclear" instead of
guessing. When citing an effect, carry its confidence label.

### Small samples behind some patterns

[Stay Cold · Google Ads · known limit · as of 2026-07-03]
BFCM insights rest on n=2 seasons measured under two different counting
regimes — not enough for seasonal thresholds. The auto-apply hit rate (~38 %)
rests on n=8 clusters. Client-side interventions median −22 % rests on n=13
clusters and is dominated by one event (the 2024-10-23 tracking-template
rollout), so it describes uncoordinated account-wide rollouts, not "the
client" as such.

### Data coverage boundaries

[Stay Cold · Google Ads · known limit · as of 2026-07-03]
Change history before July 2024 does not exist (UI export limitation; the
Google Ads API only returns 30 days of change events). Daily performance is
covered June 2023 – July 2026; the purchase-only series starts May 2024.
The Google Ads API retains daily performance for ~37 months on a rolling
basis, so the oldest months disappear over time. Daily forward capture of
change events runs since 2026-07-10, closing the change-history gap from
that date onward. Analysis cutoff for everything in this pack: 2026-07-03;
events after that date are not covered.

### The promo calendar is seeded, not complete — unverified windows may distort verdicts

[Stay Cold · Google Ads · known limit · as of 2026-07-10]
Per-change verdicts are only excluded from rule evidence where a promo window
is documented. The current promo calendar contains three windows inferred
from the change log (BFCM 2024-11-20 to 2024-12-02, BFCM 2025-11-20 to
2025-12-01, Black Spring Sale 2026-03-12 to 2026-03-20) and is NOT yet
verified or complete — e.g. possible spring/summer sales in April 2025 are
unknown. Negative verdicts dated near undocumented promos (for example the
2025-04-04/05 budget jumps) could be partially intraday scaling; they stand
as measured until the account operator completes the calendar, after which
the analysis is re-run with one command.
