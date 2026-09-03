# Stay Cold Google Ads — measurement regimes (how to read any ROAS)

### Rule zero: never trust the account-surface ROAS without checking the date

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
The Stay Cold Google Ads account (customer ID 359-911-6618) has had three
different conversion-counting regimes since 2023. A ROAS number from this
account is only meaningful together with its date. Since 2025-11-10 the
reported account ROAS is inflated by a constant factor of about 1.5× versus
real purchase revenue. Any analysis, target setting or scaling decision must
use the purchase-only series ("clean ROAS", conversion action
purchase_gads_mable) or trend-corrected deltas (DiD) — never the raw account
surface number across regime boundaries.

### Regime 1 (Aug 2023 – Apr 2024): double counting via GA4 + Shopping App

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
From August 2023 to April 2024 two purchase conversion actions were primary in
parallel: "GA4 (bereinigt)" and "Google Shopping App Purchase". They counted
largely the same orders twice. Example: February 2024 shows 410 + 435
conversions that are mostly identical purchases. Consequence: reported
conversion and revenue figures from Aug 2023 to Apr 2024 must never be used
as absolute values; only the purchase-only series or relative comparisons are
valid for that window.

### Regime 2 (May 2024 – Sep 2025): the clean window

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
From May 2024 to September 2025 only purchase_gads_mable counted as the
primary conversion. This is the only period where account-surface numbers and
real purchases agree. Use this window as the anchor for baselines and
year-over-year comparisons. The change-impact analysis of the account uses
this series as its measurement basis.

### Regime 3 (since 2025-11-10): NewCustomerPurchase inflates reported ROAS ~1.5×

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
Since 2025-11-10 a second conversion ("Custom NewCustomerPurchase - Stay Cold
Mable") counts in addition to the purchase, including its value — every
new-customer order is effectively counted twice. Measured inflation of
reported ROAS vs. clean purchase ROAS by month: Nov 2025 1.28×, Dec 2025
1.57×, Jan 2026 1.53×, Feb 1.53×, Mar 2026 1.49×, Apr 1.55×, May 1.50×,
Jun 2026 1.56×. Example June 2026: account surface shows ROAS 7.85, real
purchase ROAS is 5.04.

### The regime-3 event chain (dates that matter)

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
The double counting was introduced in steps: 2025-11-10 conversion
restructuring (purchase_gads_mable set primary, CheckoutStarted renamed
"(OLD)"); 2025-11-23 the bidding goal "Käufe" was changed to "Käufe + New
Customers" — two days before Black Friday week; 2025-12-11 NewCustomerPurchase
set back to "secondary, observe only"; 2026-02-18 account-level new-customer
acquisition setup activated ("bid for new customers only" plus a 16.46 EUR
extra conversion value per new customer); 2026-03-13 a campaign-specific goal
"Käufe + New Customers" re-included it, active until today. The NCA setup is a
deliberate strategy, not a bug — but it changes what the account ROAS measures.

### Side effect: tROAS targets are softer than their nominal value

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
Because conversion value has been inflated by roughly 1.5× since late 2025
(and additionally by the 16.46 EUR new-customer bonus since 2026-02-18), any
target-ROAS set in the account is effectively looser than its nominal number:
a tROAS of 450 % steers toward roughly 300 % on real purchase revenue. When
setting or evaluating tROAS targets on this account, convert between reported
and clean scale first.

### Practical conversion rule for agents

[Stay Cold · Google Ads · measurement · as of 2026-07-03]
To convert a reported account ROAS after 2025-11-10 into an estimate of real
purchase ROAS, divide by the month's inflation factor (range 1.49–1.57,
average ≈ 1.5). For exact work, always aggregate the purchase-only conversion
action (purchase_gads_mable) instead of converting. Before 2024-05-01, do not
convert — recompute from the purchase-only series only.
