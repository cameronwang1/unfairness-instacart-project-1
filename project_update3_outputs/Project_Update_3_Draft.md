# Project Update 3 - Instacart Popularity Bias Feedback Loops

**Team:** Cameron Wang, Kevin O'Neill  
**Research question:** Does popularity-biased recommendation create feedback loops that increasingly favor popular products while systematically crowding out niche preferences over time?

## A) What we have done since Update 2

- Finalized an observational analysis pipeline using the Instacart prior-order dataset (`3,214,874` user-orders; `206,209` users).
- Implemented product popularity segmentation based on global purchase counts:
  - `popular` = top 10% of products by global frequency (threshold: `>= 1,021` purchases).
  - `ultra-popular` = top 1% by global frequency (threshold: `>= 9,931` purchases).
- Built order-index trend metrics (by `order_number`) to test whether user baskets drift toward globally popular products over repeated shopping trips.
- Computed user-level first-vs-last comparisons for popularity concentration.
- Generated reusable result tables for plotting and inclusion in slides/writeup:
  - `trend_by_order_number.csv`
  - `trend_extra_metrics.csv`
  - `first_vs_last_summary.csv`
  - `hhi_trend_by_order_number.csv`
  - `user_delta_quantiles.csv`

## B) Preliminary results

### 1) Popular-item concentration increases over shopping history

- Average share of popular items rises from `0.792` at order 1 to `0.819` at order 20.
- Linear slope over first 20 orders: `+0.00146` popular-share points per order.
- For ultra-popular items (top 1%), share rises from `0.400` to `0.435` by order 20.
- Ultra-popular slope over first 20 orders: `+0.00204` per order.

### 2) Novelty declines (proxy)

- Mean log global popularity of purchased products increases steadily from `8.617` (order 1) to `8.810` (order 20).
- Slope over first 20 orders: `+0.01075` per order.
- Interpretation: on average, users increasingly buy products with higher global purchase frequency as order history grows.

### 3) Distributional nuance (not all users move in same direction)

- Mean first-vs-last user change in popular share: `-0.00149` (median `0.0`).
- Quantiles of user change in popular share:
  - 10th: `-0.265`
  - 25th: `-0.111`
  - 50th: `0.0`
  - 75th: `+0.111`
  - 90th: `+0.261`
- Interpretation: aggregate trends by order index show increased concentration, but user-level first-vs-last changes are heterogeneous and likely require stratification.

## C) Roadblocks and how we handled them

1. **No recommendation exposure logs (only purchases).**  
   We reframed current results as **behavioral signatures consistent with potential feedback loops**, not direct causal proof of recommender exposure.

2. **Defining niche vs popular is sensitive to threshold choice.**  
   We implemented multiple thresholds (top 10%, top 1%) and plan sensitivity checks across additional cutoff values.

3. **Diversity metric design.**  
   Within-order product uniqueness ratio was uninformative in this dataset, so we switched to concentration and popularity-based proxies (popular share, ultra-popular share, mean log popularity).

## D) Plan for next sprint (toward final presentation + final writeup)

1. Run robustness checks:
   - Alternative popularity definitions (within department/aisle and user-specific rarity).
   - Stratify by basket size, user tenure, and department mix.
   - Add placebo analyses where concentration should not increase if feedback loop narrative is weak.
2. Build a lightweight simulation/counterfactual module:
   - Compare neutral, popularity-biased, and anti-popularity ranking policies on identical synthetic user trajectories.
3. Convert observational findings + simulation results into non-technical story arc for presentation.

## E) Feedback we would like from you

1. Is it acceptable to position this stage as **evidence consistent with feedback loops** rather than causal identification, given missing exposure logs?
2. For fairness framing, should we prioritize:
   - group fairness (popular vs niche exposure), or
   - welfare framing (discovery loss and reduced choice diversity), or
   - both equally?
3. Does our planned final presentation scope (observational + simulation + implications for consumers/small producers) seem balanced for a 10-minute non-technical audience?

## F) Confirmed final presentation plan (high level)

- Audience: non-technical classmates/consumers.
- Core message: recommendation systems can unintentionally narrow choice by reinforcing already-popular products.
- Format: 10-minute slide deck with concrete visuals, plain-language interpretation, and policy/algorithm design recommendations.
