# Chart Selection Justification
## Executive Dashboard — Visualization Design Rationale

---

## Design Philosophy

Every chart was selected using a question-first process: define the business question, then choose the chart type that answers it most directly for an executive audience. Charts are information tools, not decorations.

**Five design principles applied throughout:**
1. **Question-first** — chart type follows the question, never the reverse
2. **Encode with purpose** — every color, size, and position carries meaning
3. **Sort for insight** — always sort by the metric of interest, not alphabetically
4. **Consistent risk language** — green = healthy, amber = caution, red = risk throughout
5. **Minimize cognitive load** — remove all elements that don't convey information

---

## Chart 1: Monthly Sales & Profit Trend (Combo: Bar + Dual-Axis Line)

**Question answered:** How are sales and profit trending month-by-month? Are there seasonal patterns?

**Why this chart type:** A combo chart (bars + dual-axis line) shows volume (bars for sales) and trend direction (line for profit) simultaneously. A pure line chart would make it harder to perceive absolute month-to-month sales differences. A bar-only chart would miss the profit trend overlay.

**Field usage:**
- Color: Blue bars for sales, green line for profit (matches KPI card color coding), amber dashed for margin %
- Dual Y-axis: Left for absolute ₹ values, right for margin %; both encoded in distinct colors to avoid confusion
- Sorting: Strict chronological — time-series data must never be reordered

**Design principle:** Preattentive attributes (color + position) encode two data streams simultaneously, reducing the need for mental switching between separate charts.

**Mistake avoided:** Did not use a single-axis line for both sales and profit — the scale difference (₹M vs M%) would distort both series. Did not use a pure area chart — hides month-to-month comparison.

---

## Chart 2: Year-over-Year Comparison (Grouped Bar)

**Question answered:** Did 2025 outperform 2024 on sales and profit?

**Why this chart type:** Grouped bars are the most direct mechanism for side-by-side comparison of two time periods. With only 2 years, a line chart has only 2 data points — a line between two points conveys nothing about trend direction between them.

**Field usage:** Dark vs light shading within the same color family distinguishes 2024 from 2025 without introducing confusing additional hues. Both measures (Sales, Profit) visible simultaneously.

**Mistake avoided:** Did not use a stacked bar (hides the comparison). Did not normalize to percentages (absolute values are more meaningful for executive budget planning).

---

## Chart 3: State-Level Performance (Tile/Heatmap Grid)

**Question answered:** Which states generate the most revenue? How do margins vary geographically?

**Why this chart type:** A geographic tile heatmap (cartogram) communicates spatial distribution and data simultaneously. Standard filled maps lose too much detail at India's state boundary complexity; tile grids keep every state equally readable.

**Field usage:**
- Color family: Each region has a distinct hue (East=blue, North=green, South=amber, West=purple) — consistent with regional color encoding elsewhere
- Color intensity: Proportional to sales within region
- Badge overlay: Margin % badge on each tile — enables simultaneous assessment of sales size and profit quality without requiring a second chart

**Mistake avoided:** Did not use a filled choropleth map without data labels (hard to read precise values). Did not encode margin and sales as two separate size/color channels (too complex to decode).

---

## Chart 4: Regional Sales & Profit (Horizontal Bar)

**Question answered:** Which region has the highest absolute sales and profit?

**Why this chart type:** Horizontal bars are superior to vertical bars when the primary comparison is between a small number of labeled categories (4 regions). The horizontal orientation makes the label-to-bar association clearer and the value comparison more direct.

**Field usage:** Each region bar uses its dedicated region color (consistent with tile grid). Two datasets (Sales + Profit) in same chart for direct comparison.

**Mistake avoided:** Did not use a pie chart (precise percentage comparison impossible). Did not use vertical bars (region names would require rotation and reduce readability).

---

## Chart 5: Sub-Category Profit Margin (Sorted Horizontal Bar)

**Question answered:** Which sub-categories are the most and least profitable? Where is the margin risk?

**Why this chart type:** A sorted horizontal bar is the ideal chart for ranking items on a single metric. Sorting ascending (lowest first) naturally places the problem items (Furniture Tables, Bookcases) at the top where the eye falls first — the most important items become most visible.

**Field usage:**
- Color: Red (<10%), Amber (10-15%), Green (>15%) — consistent risk color language
- Sort: Ascending margin — risk-first presentation
- Dashed reference line at 15.35% (portfolio average) enables instant categorization

**Mistake avoided:** Did not group by category first (would hide the cross-category ranking). Did not use a treemap (margin is not proportional to area — mixing margin and sales in a treemap creates false size-meaning associations).

---

## Chart 6: Category Revenue Share (Doughnut Chart)

**Question answered:** What proportion of total revenue does each category contribute?

**Why this chart type:** A doughnut chart is appropriate for part-to-whole composition with exactly 3 categories. With 3 slices, angle comparison is perceptually manageable. The high cutout reduces the angular distortion of traditional pie charts.

**Field usage:** 3 distinct colors per category (blue/green/amber) — reused from the sub-category chart for color continuity. Tooltip shows both ₹ value and % share.

**Mistake avoided:** Did not use a pie chart with more than 5 slices. Did not use a donut for sub-category breakdown (13 slices would be unreadable).

---

## Chart 7: Customer Segment Comparison (Grouped Bar + Table)

**Question answered:** How do the three customer segments compare on sales, profit, return rate, and AOV?

**Why this chart type:** Grouped bars show absolute sales and profit for direct comparison. The supplementary table below provides the precision metrics (margin %, return rate, AOV) that bars cannot encode with enough precision at the scale used.

**Field usage:** Three segment colors (blue, teal, purple). Color-coded badges in the table (green/amber/red) provide instant risk signal at a glance.

**Mistake avoided:** Did not attempt to encode all 5 metrics (sales, profit, margin, return rate, AOV) in a single chart — would create visual overload. Table + chart combination allows precision where needed and visual comparison where useful.

---

## Chart 8: Discount Band vs Profit Margin (Bar + Line Combo)

**Question answered:** How does the discount level affect profit margin? Is the impact gradual or sudden?

**Why this chart type:** A combo chart (bars for margin, line for order count) enables simultaneous assessment of financial impact AND business volume. Leadership needs to know both: "how bad is the margin at 21-30%?" and "how many orders are in that band?" A scatter plot of individual orders would be unreadable for executive audiences.

**Field usage:**
- Color: Gradient from green (no discount) to red (31%+) — visually communicates deterioration
- Zero line: Critical axis reference that makes the loss-making band visually unambiguous
- Secondary axis: Order count line shows 21-30% is the LARGEST order band — the margin collapse happens at peak volume

**Mistake avoided:** Did not omit the order count overlay (without it, a small band might be dismissed as low-impact). Did not truncate the Y-axis (would hide the -4.95% bar).

---

## Chart 9: Ship Mode Performance (Bar + Line Combo)

**Question answered:** Which shipping modes are used most? How does delivery speed relate to margin?

**Why this chart type:** Bars show volume; the red delivery-days line reveals whether faster modes correlate with higher or lower margins — a question that requires two data streams.

**Field usage:**
- Red line for delivery days (urgency encoding consistent with risk language)
- Supplementary table: Precise numbers (orders, days, margin) for operational planning

**Mistake avoided:** Did not use only a line chart (loses volume comparison). Did not use a stacked bar (obscures individual mode comparison).

---

## Chart 10: Delivery Speed Distribution (Doughnut)

**Question answered:** What proportion of orders arrive within each speed tier?

**Why this chart type:** Part-to-whole composition with 5 buckets — doughnut works because the bucket labels are intuitive and the number of slices (5) is at the upper limit of readable pie-type charts.

**Field usage:** Color gradient from green (Same Day) to red (8+ Days) communicates speed/urgency visually without additional legend explanation.

**Mistake avoided:** Did not use a bar chart (would not communicate cumulative part-to-whole composition). Did not add a sixth bucket (would exceed the readability threshold for circular charts).

---

## Chart 11: Return Rate by Category & Segment (Sorted Horizontal Bar)

**Question answered:** Which categories and segments have the highest return risk?

**Why this chart type:** A sorted horizontal bar enables direct rate comparison across two different dimensions (category + segment) in a single view. Color coding instantly communicates risk level without requiring the reader to interpret axis values.

**Field usage:**
- Red (>6%), Amber (4-6%), Green (<4%) — consistent with risk language used across the entire dashboard
- Reference line at portfolio average (4.55%) enables instant above/below comparison

**Mistake avoided:** Did not use separate pie charts per category (no cross-dimension comparison possible). Did not use a table only (visual risk encoding makes severity immediately apparent before reading numbers).

---

## Filter Design Justification

**6 filters: Year, Region, Category, Segment, Ship Mode, Campaign Channel**

**Why these 6:** They represent the six primary analytical dimensions used in every section of the dashboard. Any meaningful business question can be answered by combining at most 2-3 of these filters.

**Design choices:**
- Filters visible at top of every page view — reduces navigation friction for executives
- Filter status indicator shows count of active filters — prevents "why don't the numbers add up?" confusion
- Single Reset button — reduces friction for multi-filter exploration sessions
- Dropdown select UI — simplest interaction model for executive users; no checkbox complexity

**Cross-chart action:** All 6 filters update all connected charts simultaneously, enabling coherent drill-down: start at portfolio → apply Region=South → apply Category=Technology → see South Technology performance across all views without navigating between pages.
