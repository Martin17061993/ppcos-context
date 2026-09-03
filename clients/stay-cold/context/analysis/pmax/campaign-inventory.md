# PMax Campaign Inventory (Phase 0)

Generated: 2026-08-06  ·  business.md vertical: `ecommerce`  ·  changelog: present

**Totals:** 12 campaigns — 11 ecom / 1 lead-gen · 3 Feed-Only / 8 Full Assets · 0 mid-learning · 1 needing a clarifying question.

**Active Roster:** 7 scored & reported · 5 excluded (dormant: paused, 0 impr in window) · 0 excluded (experiment, base-only default). Excluded campaigns are pulled and listed here for completeness but are not scored or narrated.

| Campaign | Status | Report | Vertical | Setup | NCA mode | Learning | feed-integration | conversion-signal | asset-groups | brand-defense | nca-lifecycle | asset-performance | audience-signals | channel-allocation | url-expansion |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| EX I WW I PMAX I SCALING I BROAD | ENABLED | audit | ecom | full | BID_HIGHER_FOR_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I WW I PMAX I SCALING I RE/HOT | PAUSED | excl: dormant | ecom | full | TARGET_ALL_EQUALLY | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I SKANDI I PMAX I TESTING I PROSPECTING | ENABLED | audit | ecom | full | BID_HIGHER_FOR_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I FRA I PMAX I TESTING I BROAD | ENABLED | audit | ecom | full | TARGET_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I ESP I PMAX I TESTING I BROAD | PAUSED | excl: dormant | ecom | full | BID_HIGHER_FOR_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX + NEAR-INDEX | ENABLED | audit | ecom | feed-only | TARGET_NEW_CUSTOMER | stable | ✓ | null | null | ✓ | ✓ | null | null | ✓ | ✓ |
| EX I USA I PMAX I TESTING I BROAD | ENABLED | audit | ecom | full | BID_HIGHER_FOR_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I WW I PMAX I PROSPECTING I BROAD | ENABLED | audit | ecom | full | TARGET_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I WW I PMAX I PROSPECTING I RoB | PAUSED | excl: dormant | ecom | full | TARGET_NEW_CUSTOMER | stable | ✓ | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | ENABLED | audit | ecom | feed-only | TARGET_NEW_CUSTOMER | stable | ✓ | null | null | ✓ | ✓ | null | null | ✓ | ✓ |
| SMART VS ST SHOPPING TOF I HOODIE TEST | PAUSED | excl: dormant | ecom | feed-only | TARGET_NEW_CUSTOMER | stable | ✓ | null | null | ✓ | ✓ | null | null | ✓ | ✓ |
| PMAX I NC DEALS PUSH I SPLIT | PAUSED | excl: dormant | leadgen (?) | n/a | NONE | stable | null | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

Module columns: `✓` = applicable (scored), `null` = N/A-by-design (excluded from the denominator, never 0).
`Report` column: `audit` = in the Active Roster (scored & reported); `excl: dormant` = paused with 0 impressions in the window; `excl: experiment` = experiment arm excluded by default. Excluded campaigns are never scored or narrated.

## Prior decisions (pmax-decisions.json)
- no prior pmax-decisions.json — nothing to re-confirm

## Clarifying questions for the runtime
- **[vertical-conflict]** Classification signals conflict for "PMAX I NC DEALS PUSH I SPLIT". Is this an ecommerce or lead-gen campaign?
  - evidence: no listing-group / product-feed surface found on any asset group
  - evidence: account conversion actions look ecom (purchase_gads_mable)
  - evidence: business.md vertical = "ecommerce"
  - evidence: CONFLICT: signals disagree (leadgen vs ecom) — confirm with user
- **[nca-intent]** New-customer acquisition (NCA) intent is not stated in business.md. For PMax campaigns intended to acquire new customers, should NCA bidding be ON, and is there a new- vs existing-customer value/LTV premium to validate? (business.md -> ask -> write back -> SKIP value-premium if genuinely unavailable)
  - evidence: EX I WW I PMAX I SCALING I BROAD: API NCA mode = BID_HIGHER_FOR_NEW_CUSTOMER
  - evidence: EX I WW I PMAX I SCALING I RE/HOT: API NCA mode = TARGET_ALL_EQUALLY
  - evidence: EX I SKANDI I PMAX I TESTING I PROSPECTING: API NCA mode = BID_HIGHER_FOR_NEW_CUSTOMER
  - evidence: EX I FRA I PMAX I TESTING I BROAD: API NCA mode = TARGET_NEW_CUSTOMER
  - evidence: EX I ESP I PMAX I TESTING I BROAD: API NCA mode = BID_HIGHER_FOR_NEW_CUSTOMER
  - evidence: EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX + NEAR-INDEX: API NCA mode = TARGET_NEW_CUSTOMER
  - evidence: EX I USA I PMAX I TESTING I BROAD: API NCA mode = BID_HIGHER_FOR_NEW_CUSTOMER
  - evidence: EX I WW I PMAX I PROSPECTING I BROAD: API NCA mode = TARGET_NEW_CUSTOMER
  - evidence: EX I WW I PMAX I PROSPECTING I RoB: API NCA mode = TARGET_NEW_CUSTOMER
  - evidence: EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING: API NCA mode = TARGET_NEW_CUSTOMER
  - evidence: SMART VS ST SHOPPING TOF I HOODIE TEST: API NCA mode = TARGET_NEW_CUSTOMER
  - Unresolved acquisition strategy routes to strategy-specialist (plan NCA ladder).
