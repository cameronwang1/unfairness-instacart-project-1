# Final Presentation Skeleton (10 minutes)

## Slide 1 - Title and one-sentence thesis (0:30)
- **Title:** "When Recommendations Narrow Choice: Popularity Feedback Loops in Instacart"
- Thesis: "As users place more orders, purchases become increasingly concentrated in globally popular products, which may reduce discovery of niche items."

## Slide 2 - Why this matters (1:00)
- Real-world hook: online grocery shopping increasingly mediates product discovery.
- Stakeholders:
  - Consumers (variety, discovery, dietary fit).
  - Small/local producers (visibility and market access).
- Key risk: "rich-get-richer" dynamics in recommendations.

## Slide 3 - Research question and framing (0:45)
- Primary question from proposal.
- Clarify scope: we observe purchasing outcomes, not direct recommendation exposure logs.
- What we can conclude now: patterns consistent with potential feedback loops.

## Slide 4 - Data and definitions (1:00)
- Dataset size: 206,209 users; 3,214,874 prior user-orders.
- Definitions:
  - popular = top 10% by global purchase count.
  - ultra-popular = top 1%.
- Outcome metrics:
  - popular-item share per order.
  - ultra-popular share per order.
  - mean log product popularity per order.

## Slide 5 - Main trend visual: popular share vs order number (1:00)
- Show line chart (orders 1-20).
- Talk track:
  - "Popular share rises from ~79.2% to ~81.9%."
  - "Trend is upward and persistent across early-to-mid user history."

## Slide 6 - Main trend visual: ultra-popular concentration (1:00)
- Show line chart (orders 1-20).
- Talk track:
  - "Top-1% product share rises from ~40.0% to ~43.5%."
  - "Concentration intensifies for the highest-frequency products."

## Slide 7 - User heterogeneity (1:00)
- Show distribution/quantiles of first-vs-last changes.
- Talk track:
  - Not every user drifts the same way.
  - Median change is 0; tails are substantial in both directions.
  - Motivates stratified and causal follow-up work.

## Slide 8 - Limits and methodological honesty (1:00)
- No exposure data; purchase-only observational design.
- Alternative explanations: staples, lifecycle, household changes.
- Explain safeguards:
  - within-user comparisons,
  - sensitivity to definitions,
  - planned placebo and robustness checks.

## Slide 9 - Next step: simulation for mechanism testing (1:00)
- Compare policy families:
  - neutral baseline,
  - popularity-biased ranking,
  - anti-popularity/diversity-aware ranking.
- Evaluate long-run concentration and niche visibility under each.

## Slide 10 - Implications and recommendations (1:00)
- If trend persists:
  - add calibrated exploration,
  - cap popularity reinforcement,
  - report exposure parity for niche categories.
- Close with practical takeaway for product teams and policy-minded stakeholders.

## Backup slides (optional)
- Extra robustness tables by category/department.
- Threshold sensitivity results (top 5%, 10%, 20%, etc.).
- Technical appendix for metric formulas.
