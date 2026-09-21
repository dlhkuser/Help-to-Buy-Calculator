# Help to Buy Calculator

A single-page calculator that models an Australian Government **Help to Buy** shared-equity
purchase against an ordinary home loan on the same property — repayments, offset behaviour,
WA stamp duty, and what the Government's equity share actually costs you over time.

Defaults are set for an **$850,000 Perth purchase** (the WA metropolitan price cap).

Open `index.html` in a browser. No build step, no dependencies, no server required.

## What it models

| | |
|---|---|
| **Help to Buy** | Government contributes up to 30% (existing home) or 40% (new build). You own the home; they hold an equity share. |
| **Ordinary loan** | Same property and deposit, no Government contribution. Stands in for the 5% Deposit Scheme. |

Both scenarios run through the same amortisation engine so the comparison is like-for-like.

### Offset

Interest each period is charged on `balance − offset`, so extra contributions reduce interest
rather than the repayment. Once the offset covers the debt:

- interest falls to zero,
- further contributions stop (there is nothing left to offset),
- the loan is **not** discharged by default — the full repayment continues and the remaining
  balance is carried interest-free until it clears, leaving the offset liquid.

A *Discharge* toggle closes the loan at that crossover instead, for comparison.

### Break-even

Help to Buy costs you the Government's slice of the growth and saves you interest. Setting the
two equal gives:

```
break-even value = purchase price + (interest saved ÷ Government's %)
```

Below that value at exit, the scheme has cost less than an ordinary loan. The page also derives
the **growth ceiling** — the annual capital growth you can tolerate and still come out ahead —
which falls the longer you hold, because their share compounds while the interest saving stops.

### When to buy them out

The Government's equity accrues at the property's growth rate; mortgage money accrues at your
interest rate. Spare cash should go against the dearer of the two, so the rule is simply
**growth vs. interest rate** — there is no value threshold. Break-even is exactly where the two
rates meet.

## Stamp duty

WA transfer duty is calculated from the property value using the rates in force from
**7 May 2026**, with a manual override.

**General rate**

| Dutiable value | Duty |
|---|---|
| $0 – $120,000 | $1.90 per $100 |
| $120,001 – $150,000 | $2,280 + $2.85 per $100 over $120,000 |
| $150,001 – $360,000 | $3,135 + $3.80 per $100 over $150,000 |
| $360,001 – $725,000 | $11,115 + $4.75 per $100 over $360,000 |
| $725,001+ | $28,453 + $5.15 per $100 over $725,000 |

**First home owner rate** — exempt to $600,000, concessional at $16.15 per $100 to $800,000,
general rate above that. An $850,000 purchase therefore gets **no concession** and pays the full
general rate of **$34,890.50**.

## Features

- English / 繁體中文 throughout, including dynamic text and date formatting
- Weekly, fortnightly or monthly repayment periods, with a dated schedule
- Per-period and yearly-aggregate views; interest-free periods marked in green
- Inputs persist to `localStorage` (saved on blur, not on keystroke) with a reset
- Mobile layout: hamburger nav showing one section at a time, fixed Prev/Next bar
- Light and dark themes

## Price caps (WA)

| | Perth metro | Rest of WA |
|---|---|---|
| Help to Buy | $850,000 | $600,000 |
| 5% Deposit Scheme | $850,000 | $600,000 |

## Caveats

This is an estimate, not financial advice. Help to Buy has a hard income cap
($103,000 single / $165,000 joint, no exemptions), requires Australian citizenship, and
requires you to contribute your maximum reasonable deposit — if your savings and borrowing
capacity alone reach the purchase price, you are not eligible.

Income thresholds are wage-indexed annually; the figures above reflect the FY2026 Notice of
Assessment basis. Confirm everything with a Participating Lender.

Source: <https://firsthomebuyers.gov.au>
