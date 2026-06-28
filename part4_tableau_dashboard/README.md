# Part 4: Tableau Executive Dashboard
## Retail Sales Performance 2024–2025

---

## 1. Business Problem Summary

A retail leadership team needs an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns.

The dashboard must help leadership identify business opportunities and risks — not just display charts. It must tell a clear business story and support decision-making.

**Key business questions the dashboard answers:**
- Where is revenue and profit growing or declining over time?
- Which regions, categories, and sub-categories drive the most profit?
- Are discounts helping or hurting profitability?
- Which shipping modes are causing delays?
- Where are returns concentrated and why?
- Which customer segment is most valuable?

---

## 2. Dataset Description

**File:** `data/dashboard_sales_data.xlsx`
**Total Records:** 4,200 orders
**Date Range:** January 2024 – December 2025
**Geography:** India (state-level)

| Field | Type | Description |
|-------|------|-------------|
| Order ID | String | Unique order identifier |
| Order Date | Date | Date order was placed |
| Ship Date | Date | Date order was shipped |
| Customer ID | String | Unique customer identifier |
| Customer Segment | Categorical | Consumer, Corporate, Home Office |
| Region | Categorical | North, South, East, West |
| State | Categorical | State name (India) |
| City | Categorical | City name |
| Category | Categorical | Furniture, Office Supplies, Technology |
| Sub Category | Categorical | 13 sub-categories |
| Product Name | String | Product name |
| Ship Mode | Categorical | Same Day, First Class, Second Class, Standard Class |
| Sales | Numeric | Revenue in currency |
| Quantity | Integer | Units ordered |
| Discount | Numeric | Discount rate (0 to 1) |
| Profit | Numeric | Profit (can be negative) |
| Return Flag | Binary | 1 = returned, 0 = not returned |
| Delivery Days | Integer | Days from order to delivery |
| Customer Rating | Numeric | Rating 1–5 |
| Campaign Channel | Categorical | Organic, Social, Referral, Paid, Email, null |

---

## 3. Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`
**Tool:** Tableau Public (Desktop)

The workbook contains 9 individual sheets and 1 executive dashboard:

| Sheet Name | Chart Type | Purpose |
|------------|------------|---------|
| Sales Trend View | Dual-axis Line Chart | Monthly Sales and Profit trend over 2024–2025 |
| Regional Performance View | Filled Map (Choropleth) | State-level sales heat map |
| Regional Bar Chart | Horizontal Bar Chart | Region-wise Sales and Profit comparison |
| Category Profitability View | Treemap | Category/Sub-category Sales (size) and Profit Margin (color) |
| Category Bar Chart | Horizontal Bar Chart | Sub-category profit ranking |
| Customer Segment View | Side-by-Side Bar Chart | Sales and Profit by customer segment |
| Shipping Performance View | Horizontal Bar Chart | Average delivery days by ship mode |
| Discount vs Profit View | Scatter Plot | Relationship between discount rate and profit |
| Return Analysis View | Highlight Table | Return rate by Sub-category and Customer Segment |

**Dashboard Name:** `Executive Sales Dashboard`

---

## 4. Calculated Fields Created

| Field Name | Formula | Purpose |
|------------|---------|---------|
| Profit Margin | `SUM([Profit]) / SUM([Sales])` | Profitability ratio per view |
| Cost | `[Sales] - [Profit]` | Derived cost field |
| Average Order Value | `SUM([Sales]) / COUNTD([Order ID])` | Revenue per unique order |
| Return Rate | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of returned orders |
| Shipping Delay Bucket | `IF [Delivery Days] <= 1 THEN "Same Day" ELSEIF [Delivery Days] <= 3 THEN "Fast (2-3d)" ELSEIF [Delivery Days] <= 5 THEN "Standard (4-5d)" ELSE "Delayed (6d+)" END` | Delivery speed categorization |

---

## 5. Dashboard Components

**Title:** Executive Sales Dashboard | Retail Sales Performance 2024–2025

**KPI Summary Row (5 cards):**
- Total Sales: $217.0M
- Total Profit: $33.3M
- Profit Margin: 15.3%
- Return Rate: 4.5%
- Average Order Value: $51,671

**Charts on Dashboard (9 total):**
1. Sales Trend View — full width, top
2. Regional Performance Map — left middle
3. Regional Bar Chart — right middle
4. Customer Segment View — left lower
5. Category Bar Chart — right lower
6. Shipping Performance View
7. Discount vs Profit Scatter
8. Return Analysis Highlight Table
9. Category Profitability Treemap

---

## 6. Filters and Interactions Used

**Interactive Filters (applied to all sheets):**
| Filter | Field | Type |
|--------|-------|------|
| Region | Region | Multi-select dropdown |
| Sub Category | Sub Category | Multi-select dropdown |
| Customer Segment | Customer Segment | Multi-select dropdown |

**Action Filters:**
- Clicking any state on the Regional Map → filters all other charts to that state automatically (Tableau default dashboard action)
- Clicking any bar or data point → highlights and filters related data across connected sheets

---

## 7. Key Business Insights

1. **Technology drives 84% of total profit** at an 18.2% margin — Copiers ($7.31M) and Accessories ($7.19M) are the top sub-categories
2. **South region leads** with $64.7M in sales and $9.99M in profit — highest of all 4 regions
3. **Discounts destroy profit** — scatter plot shows clear negative correlation; orders with 30%+ discount frequently produce losses
4. **Standard Class shipping is 12x slower** than Same Day (4.71 days vs 0.40 days) — creating delivery risk
5. **Furniture has the highest return rates** — Chairs in Home Office segment at 13.7% is the worst combination
6. **Home Office segment edges ahead** at $74.5M sales and $11.6M profit vs Corporate's $70.6M and $10.7M
7. **4.3% YoY growth** from 2024 ($106.2M) to 2025 ($110.8M) with stable margins
8. **Furniture margin is only 6.9%** vs Technology's 18.2% — Furniture economics need urgent review

---

## 8. Dashboard Story Summary

The business is profitable and growing, but unevenly. Technology is the engine; Furniture is the drag. South leads regionally; West and East have room to improve. Discounting without guardrails is the biggest controllable risk — many orders are loss-making due to high discounts. Standard Class shipping delays are contributing to elevated return rates especially in Furniture. Three priority actions for leadership: implement discount floor policy, rationalize Furniture portfolio, and auto-upgrade high-value orders to faster shipping.

Full story available in: `outputs/dashboard_story.md`

---

## 9. Assumptions and Limitations

**Assumptions:**
- Dataset geography is India — map shows Indian states (not US)
- `return_flag` = 1 means the order was returned
- `delivery_days` represents order-to-delivery time (not order-to-ship)
- Null values in `campaign_channel` treated as unknown/direct channel
- All currency values are in the same denomination (assumed local currency)
- KPI card values on dashboard are static text (total dataset values, do not change with filters)

**Limitations:**
- No customer retention or lifetime value data available
- Return cost (reverse logistics) is not quantified — return rate is count-based only
- ~5% of orders have missing campaign channel attribution
- No external industry benchmarks for margin or return rate comparison
- Customer ratings may have selection bias (not all customers rated)

---

## 10. Screenshots Included

| File | What It Shows |
|------|--------------|
| `screenshots/full_dashboard.png` | Complete executive dashboard with all charts and KPI row |
| `screenshots/sales_trend_view.png` | Dual-axis line chart showing Sales and Profit trend 2024–2025 |
| `screenshots/regional_performance_view.png` | Regional map and bar chart showing state/region performance |
| `screenshots/category_profitability_view.png` | Treemap and bar chart showing category and sub-category profitability |
| `screenshots/filter_interaction_view.png` | Dashboard with active filter applied showing interaction |

