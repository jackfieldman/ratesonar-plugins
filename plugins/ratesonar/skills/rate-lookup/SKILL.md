---
name: rate-lookup
description: Answer questions about the interest rates Australian banks and lenders advertise, and about RBA market curves, with the RateSonar tools. Give the date of each rate.
---

# Rate lookup with RateSonar

RateSonar keeps a daily record of advertised Australian bank and lender rates from 12 June 2026.
It also keeps dated RBA market curves. Every tool only reads data.

## Pick the tool

| Question | Tool |
|---|---|
| A lender's product, by name | `find_products` (gives `institution_id` and `product_id`) |
| Best current rates for a product type | `compare_rates` |
| One product's rate over time | `rate_history` (needs both ids from `find_products`) |
| One product's tiers, bonus conditions and fees | `rate_details` (needs both ids) |
| Recent rises, cuts, new or withdrawn products | `rate_changes` |
| A standard series or a spread, such as variable home loan minus the RBA cash rate | `list_series`, then `series` |
| One bank's prices against its peers | `bank_position`, then `bank_analysis` for a reading |
| Bond yields and the RBA's zero, forward and discount curves | `yield_curve` |
| Are the curve sources current? | `curve_pipeline_status` |

A product is the pair (`institution_id`, `product_id`). Always pass both ids.

## Report the result

1. Give each rate with its `observed_date`.
2. A point with status `carried-forward` repeats the last recorded rate. Say that no new record exists for that day.
3. A point with status `derived` (a spread or a median) is calculated, not recorded.
4. RateSonar has no record before 12 June 2026. For an earlier date, say so and give no figure.
5. These are advertised rates. Do not present them as advice for the person's situation. For an application, send the person to the lender.
6. If a tool says a usage limit was reached, give the person its message. Signing in to RateSonar raises the limit.

## Examples

- "What is the highest 12-month term deposit rate in Australia right now?" → `compare_rates` with category `term_deposit` and `termMonths` 12.
- "How has CBA's standard variable home loan rate changed since June?" → `find_products`, then `rate_history`.
- "Which lenders changed home loan rates in the last 7 days?" → `rate_changes` with category `home_loan` and `sinceDays` 7.
- "What do I need to do to get the bonus rate on ING Savings Maximiser?" → `find_products`, then `rate_details`.
- "How far above the RBA cash rate is CBA's variable rate this month?" → `series` with slug `spread.hl.var-cash`.
