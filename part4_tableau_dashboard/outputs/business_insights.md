# Business Insights — Executive Sales Dashboard

## Calculated Fields Created in Tableau

| Field Name | Formula | Purpose |
|------------|---------|---------|
| Profit Margin | `SUM([Profit]) / SUM([Sales])` | Shows profitability ratio per category, region, segment |
| Cost | `[Sales] - [Profit]` | Derives cost from sales and profit |
| Average Order Value | `SUM([Sales]) / COUNTD([Order ID])` | Revenue per unique order |
| Return Rate | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of returned orders |
| Shipping Delay Bucket | `IF [Delivery Days] <= 1 THEN "Same Day" ELSEIF [Delivery Days] <= 3 THEN "Fast (2-3d)" ELSEIF [Delivery Days] <= 5 THEN "Standard (4-5d)" ELSE "Delayed (6d+)" END` | Categorizes delivery speed into tiers |

---

## 8 Business Insights

---

### Insight 1 — Sales Trend: Steady Growth with Seasonal Spikes

**Observation from Dashboard:**
The Sales Trend View (dual-axis line chart) shows monthly sales and profit from January 2024 to December 2025 with visible Q4 peaks each year.

**Data Evidence:**
- 2024 total sales: $106.2M → 2025 total sales: $110.8M = +4.3% YoY growth
- Profit held steady at ~15.3% margin across both years
- Q4 months consistently show the highest sales spikes on the trend line

**Business Interpretation:**
The business is growing steadily. Q4 seasonality is predictable and should be planned for in terms of inventory and staffing. Margins are stable but not improving — there is no organic margin expansion happening.

**Recommended Action:**
Begin Q4 planning 60 days earlier. Explore discount rationalization to push margin above 16% in 2026.

---

### Insight 2 — Regional Performance: South Leads, East Slightly Behind

**Observation from Dashboard:**
The Regional Bar Chart shows South generating the highest sales and profit of all 4 regions.

**Data Evidence:**
| Region | Sales | Profit |
|--------|-------|--------|
| South | $64.7M | $9.99M |
| North | $54.6M | $8.31M |
| West | $48.9M | $7.40M |
| East | $48.9M | $7.60M |

**Business Interpretation:**
South is the strongest market. West and East are nearly tied in sales but East has slightly better profit — suggesting West may have higher discount rates or worse product mix.

**Recommended Action:**
Audit West region discount practices. Identify whether Furniture is over-represented in West orders and redirect focus toward Technology sales there.

---

### Insight 3 — Category Profitability: Technology Dominates, Furniture Drags

**Observation from Dashboard:**
The Category Bar Chart shows Technology sub-categories (Copiers, Accessories, Phones, Machines) occupying all top 4 profit positions. The Treemap shows Furniture tiles in red (low margin).

**Data Evidence:**
| Category | Sales | Profit | Margin |
|----------|-------|--------|--------|
| Technology | $153.9M | $28.0M | 18.2% |
| Office Supplies | $11.5M | $1.7M | 14.9% |
| Furniture | $51.6M | $3.6M | 6.9% |

- Copiers alone: $7.31M profit
- Tables: lowest profit in Furniture

**Business Interpretation:**
Furniture consumes shipping and warehouse resources but generates only 6.9 cents per dollar of profit. Technology is clearly the engine driving business profitability.

**Recommended Action:**
Reduce discounts on Furniture. Consider eliminating lowest-margin SKUs (especially Tables). Invest marketing budget in Technology upsells.

---

### Insight 4 — Customer Segment: All Three Segments Perform Similarly

**Observation from Dashboard:**
The Customer Segment View shows side-by-side bars for all 3 segments — Home Office, Consumer, Corporate — with very similar heights in both Sales and Profit.

**Data Evidence:**
| Segment | Sales | Profit |
|---------|-------|--------|
| Home Office | $74.5M | $11.6M |
| Consumer | $71.9M | $11.0M |
| Corporate | $70.6M | $10.7M |

**Business Interpretation:**
No segment significantly outperforms others. Home Office edges ahead slightly. Corporate — which typically receives more sales resources — is actually the lowest performer, suggesting potential inefficiency in B2B investment.

**Recommended Action:**
Launch a Corporate Technology account program with repeat-purchase incentives. Identify top Home Office buyers for a loyalty program.

---

### Insight 5 — Discount Impact: Higher Discounts Consistently Destroy Profit

**Observation from Dashboard:**
The Discount vs Profit scatter plot shows a clear downward trend — as discount increases, profit decreases. Many high-discount orders fall below the Y=0 line (loss-making).

**Data Evidence:**
- Negative correlation between discount and profit visible across all 3 categories
- Orders with 30%+ discount frequently show negative profit values
- All 3 trend lines (Technology, Furniture, Office Supplies) slope downward

**Business Interpretation:**
Discounting is being applied without profit floor guardrails. High discounts on already low-margin Furniture products turn orders into losses. Even Technology orders become less profitable with heavy discounting.

**Recommended Action:**
Set a minimum margin floor policy — no discount approved if resulting margin drops below 10%. Flag orders with discount > 25% for manager review.

---

### Insight 6 — Shipping Performance: Standard Class is 12x Slower than Same Day

**Observation from Dashboard:**
The Shipping Performance View (horizontal bar chart) shows Standard Class averaging 4.714 delivery days vs Same Day at 0.402 days. Bars are colored green to red showing speed gradient.

**Data Evidence:**
| Ship Mode | Avg Delivery Days |
|-----------|------------------|
| Same Day | 0.402 |
| First Class | 1.773 |
| Second Class | 2.682 |
| Standard Class | 4.714 |

**Business Interpretation:**
Standard Class is likely the most used mode due to cost savings but creates significant delivery delay risk. Delayed deliveries likely contribute to higher return rates especially for Furniture.

**Recommended Action:**
Auto-upgrade orders over $500 to First Class. For Furniture, evaluate whether Standard Class savings are offset by elevated returns.

---

### Insight 7 — Return Patterns: Chairs (Home Office) Has Highest Return Rate at 13.7%

**Observation from Dashboard:**
The Return Analysis highlight table shows Chairs × Home Office segment as the darkest red cell — highest return rate at 13.7%.

**Data Evidence:**
- Chairs × Home Office: 13.7% return rate
- Furniture category overall: highest return rates across the table
- Technology rows: consistently lightest color (lowest returns)
- Overall return rate: 4.5%

**Business Interpretation:**
Furniture returns — especially Chairs in Home Office segment — are likely driven by sizing/fit issues. Home Office buyers may be purchasing chairs without proper measurements. Each return on a low-margin Furniture item likely results in a net loss.

**Recommended Action:**
Add size guides and dimension details to Furniture product pages. Introduce a pre-purchase checklist for large Furniture items targeting Home Office buyers specifically.

---

### Insight 8 — Business Risk: Furniture + High Discount + Standard Class = Guaranteed Loss

**Observation from Dashboard:**
Combining insights from Category Bar Chart, Discount vs Profit scatter, Shipping Performance, and Return Analysis reveals a dangerous combination of risk factors concentrated in Furniture orders.

**Data Evidence:**
- Furniture margin: only 6.9%
- Discount of 30% on Furniture → margin drops to near zero or negative
- Standard Class delivery → higher return probability
- Furniture return rate: highest of all categories
- Return cost (reverse logistics + restocking) further erodes already thin margins

**Business Interpretation:**
A Furniture order with a high discount shipped Standard Class is structurally loss-making when returns are factored in. This pattern is invisible in top-line KPIs but is quietly eroding profitability at the order level.

**Recommended Action:**
Create a business rule flagging orders where: Category = Furniture AND Discount > 20% AND Ship Mode = Standard Class. Route these for approval before processing. Implement category-specific discount caps immediately.

