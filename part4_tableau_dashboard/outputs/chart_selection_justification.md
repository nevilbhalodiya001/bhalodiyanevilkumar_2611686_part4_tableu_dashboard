# Chart Selection Justification
### Executive Sales Dashboard — Why Each Chart Was Chosen

---

## Chart 1: Sales Trend View — Dual-Axis Line Chart

**1. What question does this chart answer?**
How are sales and profit changing month by month over 2024–2025? Are they growing together or diverging?

**2. Why is this chart type appropriate?**
A line chart is the standard for time-series data. It shows trends, seasonality, and direction of change clearly. A dual-axis design lets us plot Sales (left Y-axis) and Profit (right Y-axis) on the same chart without one overwhelming the other — so leadership can see if the gap between them is widening (margin compression) or stable.

**3. Fields used for color, size, label, filter:**
- X-axis: Month of Order Date
- Left Y-axis: SUM(Sales) — blue line
- Right Y-axis: SUM(Profit) — orange line
- Color: Measure Names (blue = Profit, orange = Sales)
- Filters: Region, Category, Customer Segment, Order Date

**4. What design principle was applied?**
Show trend not just totals. A bar chart of annual totals would hide the monthly seasonality and Q4 spikes that are critical for planning. The line chart makes the business cycle visible at a glance.

**5. What mistake was avoided?**
Avoided a stacked area chart — stacking Sales and Profit would imply they add up to something meaningful, which they don't. They are separate measures on different scales. Dual-axis lines represent this accurately.

---

## Chart 2: Regional Performance View — Filled Map (Choropleth)

**1. What question does this chart answer?**
Which states and regions generate the most sales? Where is the business strongest geographically?

**2. Why is this chart type appropriate?**
A filled map encodes geographic data spatially — exactly what this question requires. Darker color = higher sales. Leadership can instantly see regional concentration without reading a table. Geography is the variable; the map communicates it naturally.

**3. Fields used for color, size, label, filter:**
- Geography: State (geographic role = State/Province)
- Color: SUM(Sales) — sequential color palette (light to dark)
- Tooltip: State name, Sales, Profit
- Filters: Region, Category, Customer Segment
- Action: Clicking a state filters all other dashboard charts

**4. What design principle was applied?**
Let geography speak first. The map creates an instant visual impression of where the business is concentrated. The action filter on click adds interactivity — making it the primary navigation tool on the dashboard.

**5. What mistake was avoided?**
Avoided a pie chart of regional sales — pie charts make proportion comparison nearly impossible for human perception. The map plus bar chart combination is far more readable and actionable.

---

## Chart 3: Regional Bar Chart — Horizontal Bar Chart

**1. What question does this chart answer?**
What are the exact sales and profit numbers for each region? Which region ranks highest?

**2. Why is this chart type appropriate?**
While the map shows geography, the bar chart provides precise numeric comparison. Horizontal bars allow the region names to be read easily without rotation. Sorted descending by sales makes ranking immediately clear.

**3. Fields used for color, size, label, filter:**
- Rows: Region (sorted by SUM(Sales) descending)
- Columns: SUM(Sales) and SUM(Profit) side by side
- Color: Measure Names (orange = Sales, blue = Profit)
- Labels: Exact values shown on each bar
- Filters: Same as map (applied globally)

**4. What design principle was applied?**
Appropriate sorting — bars ranked by Sales descending so South appears first immediately confirming it as the top region. Labels added for precision so exact values don't need to be estimated from the axis.

**5. What mistake was avoided?**
Avoided combining map and bar chart on one sheet — that creates a messy dual-view. Keeping them as two separate sheets placed side by side on the dashboard is cleaner and easier to interact with.

---

## Chart 4: Category Profitability View — Treemap

**1. What question does this chart answer?**
Which categories and sub-categories are the biggest contributors to sales, and which are most and least profitable?

**2. Why is this chart type appropriate?**
A treemap encodes two dimensions simultaneously — size (Sales = tile area) and color (Profit Margin = tile color). Technology's dominance is immediately visible because its tiles are enormous. Red tiles (low margin) stand out immediately without needing to read numbers.

**3. Fields used for color, size, label, filter:**
- Size: SUM(Sales)
- Color: Profit Margin — Red-Green Diverging palette (red = low/negative, green = high)
- Label: Sub Category name + Profit value
- No rows or columns — everything on Marks card only

**4. What design principle was applied?**
Part-to-whole visualization with performance overlay. The size shows revenue contribution while color shows profitability — two business questions answered in one view. Red Furniture tiles immediately flag a problem without needing explanation.

**5. What mistake was avoided?**
Avoided a text table (cross-tab) — that would require reading every number to understand performance. The treemap makes the pattern (Technology = big and green, Furniture = smaller and red) visible in seconds.

---

## Chart 5: Category Bar Chart — Horizontal Bar Chart

**1. What question does this chart answer?**
Which specific sub-categories generate the most profit? How do they rank against each other?

**2. Why is this chart type appropriate?**
Bar charts are ideal for ranking a list of items on a single measure. 13 sub-categories ranked by profit gives leadership a clear priority list — invest in Copiers, worry about Tables. Horizontal layout makes all 13 sub-category names readable.

**3. Fields used for color, size, label, filter:**
- Rows: Sub Category (sorted by SUM(Profit) descending)
- Columns: SUM(Profit)
- Color: Category (Technology = red, Furniture = blue, Office Supplies = orange)
- Labels: Exact profit values on each bar

**4. What design principle was applied?**
Consistent color usage — the same category colors used in the treemap are repeated here. Leadership can cross-reference between the two charts using color as the linking signal.

**5. What mistake was avoided?**
Avoided sorting alphabetically by sub-category name — that would hide the ranking story completely. Sorting by profit descending makes the "Copiers first, Paper last" narrative immediately visible.

---

## Chart 6: Customer Segment View — Side-by-Side Bar Chart

**1. What question does this chart answer?**
How do Consumer, Corporate, and Home Office segments compare in Sales and Profit?

**2. Why is this chart type appropriate?**
Side-by-side grouped bars allow direct comparison of 3 segments across 2 measures simultaneously. Each segment's Sales bar sits next to its Profit bar — making the relative sizes easy to compare visually.

**3. Fields used for color, size, label, filter:**
- Columns: SUM(Sales) and SUM(Profit) side by side
- Rows: Customer Segment
- Color: Customer Segment (each segment gets its own color)
- Labels: Exact values shown on each bar
- Filters: Region, Category applied globally

**4. What design principle was applied?**
Clear hierarchy — Sales bars are longer (higher values) and sit next to the shorter Profit bars, creating a natural visual ratio that shows how much of sales becomes profit for each segment.

**5. What mistake was avoided?**
Avoided a radar/spider chart — spider charts are notoriously difficult to interpret accurately. Grouped horizontal bars give unambiguous comparison with no perceptual distortion.

---

## Chart 7: Shipping Performance View — Horizontal Bar Chart

**1. What question does this chart answer?**
Which shipping modes cause the most delivery delays? How does speed vary across ship modes?

**2. Why is this chart type appropriate?**
A horizontal bar chart comparing 4 shipping modes on one measure (average delivery days) is the clearest possible visualization. Sorted from slowest to fastest, with color gradient from red (slow) to green (fast), the ranking is instant.

**3. Fields used for color, size, label, filter:**
- Rows: Ship Mode (sorted by AVG Delivery Days descending)
- Columns: AVG(Delivery Days)
- Color: AVG(Delivery Days) — Red-Green Diverging reversed (red = slow, green = fast)
- Labels: Exact average delivery days on each bar

**4. What design principle was applied?**
Color reinforcement — the color gradient (red = bad, green = good) aligns with universal mental models. Standard Class being the longest and reddest bar immediately communicates it as the problem mode without requiring the viewer to read the numbers first.

**5. What mistake was avoided?**
Avoided a line chart — Ship Mode is a categorical variable with no natural sequential order. A line would falsely imply a continuous relationship between shipping modes. Bars are correct for categorical comparison.

---

## Chart 8: Discount vs Profit View — Scatter Plot

**1. What question does this chart answer?**
Does discounting hurt profitability? What is the relationship between discount rate and profit at the individual order level?

**2. Why is this chart type appropriate?**
A scatter plot is the only chart that can reveal correlation between two continuous variables. Each dot = one order. The downward sloping trend lines across all categories prove the negative relationship. No other chart type can show this relationship.

**3. Fields used for color, size, label, filter:**
- X-axis: Discount (disaggregated — each order is one dot)
- Y-axis: Profit (disaggregated)
- Color: Category (Technology = red, Furniture = blue, Office Supplies = orange)
- Size: SUM(Sales) — larger dot = bigger order
- Trend lines: Linear, one per category
- Reference line: Y = 0 (break-even line)
- Aggregate Measures: turned OFF to show individual orders

**4. What design principle was applied?**
Show individual data, not just averages. Turning off aggregate measures reveals that many individual orders are loss-making (below Y=0) — something a bar chart of averages would completely hide. The trend lines add statistical grounding to the visual pattern.

**5. What mistake was avoided?**
Avoided a bar chart of "average profit by discount bucket" — averaging hides the loss-making orders and creates a misleadingly smooth curve. The scatter plot shows the full distribution and makes outliers visible.

---

## Chart 9: Return Analysis View — Highlight Table

**1. What question does this chart answer?**
Where are returns concentrated? Which sub-category and customer segment combinations have the highest return risk?

**2. Why is this chart type appropriate?**
A highlight table (heat map cross-tab) shows one metric across two categorical dimensions simultaneously. Category/Sub-Category on rows, Customer Segment on columns — each cell colored by return rate. The darkest cell (Chairs × Home Office at 13.7%) is immediately the viewer's focus.

**3. Fields used for color, size, label, filter:**
- Rows: Category, Sub Category
- Columns: Customer Segment
- Color: Return Rate — Orange-Red sequential palette (light = low, dark red = high)
- Label: Return Rate % value in each cell
- Mark type: Square

**4. What design principle was applied?**
Make worst outliers impossible to miss. The darkest cell draws the eye instantly — no need to scan every number. Numeric labels in cells provide precision without requiring color estimation.

**5. What mistake was avoided?**
Avoided using return counts instead of return rate — a high-volume category would always show more returns by count even if its rate is lower. Return Rate (returns ÷ total orders) normalizes for volume and gives an accurate, fair comparison across all sub-categories.

