# Retail Executive Dashboard
## Sales Performance Analysis — 2024–2025

---

## Business Problem Summary

Leadership needs a single executive dashboard to monitor sales performance, profitability, customer segment behavior, category performance, shipping efficiency, discount impact, and return patterns. The dashboard must tell a connected business story — not present isolated charts — and support decisions on where to invest, where to cut costs, and where risks are building.

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Records:** 4,200 orders · 2 years (Jan 2024 – Dec 2025) · 20 Indian states

| Column | Type | Description |
|--------|------|-------------|
| order_id | String | Unique order ID |
| order_date | Date | Order placement date |
| ship_date | Date | Shipment date |
| customer_id | String | Customer identifier |
| customer_segment | Categorical | Consumer / Corporate / Home Office |
| region | Categorical | North / South / East / West |
| state | Categorical | 20 states |
| city | Categorical | City |
| category | Categorical | Furniture / Office Supplies / Technology |
| sub_category | Categorical | 13 sub-categories |
| product_name | String | Product name |
| ship_mode | Categorical | Standard / First / Second Class / Same Day |
| sales | Numeric | Order revenue (₹) |
| quantity | Integer | Units |
| discount | Numeric | Discount rate (0–0.5) |
| profit | Numeric | Order profit (₹, can be negative) |
| return_flag | Binary | 1 = returned |
| delivery_days | Integer | Days from order to delivery |
| customer_rating | Numeric | 1–5 rating (32 missing) |
| campaign_channel | Categorical | Organic/Paid/Email/Social/Referral (24 missing) |

---

## Tableau Workbook Description

**TWBX file:** `tableau/executive_dashboard.twbx`  
A Tableau Packaged Workbook containing:
- The workbook XML (`executive_dashboard.twb`) with all calculated fields, 7 worksheets, and 1 executive dashboard
- The data source (`Data/dashboard_sales_data.xlsx`)

**Interactive dashboard:** `tableau/executive_dashboard.html`  
An equivalent interactive HTML dashboard (Chart.js) that replicates all Tableau views with 6 live filters. Open in any modern browser.

**Worksheets included:**
1. Sales Trend View
2. Regional Performance
3. Category Profitability
4. Customer Segments
5. Shipping Performance
6. Discount vs Profit
7. Return Analysis

---

## Calculated Fields Created

| Field | Tableau Formula | Purpose |
|-------|----------------|---------|
| **Profit Margin** | `SUM([profit])/SUM([sales])` | Core profitability KPI |
| **Cost** | `[sales]-[profit]` | Estimated COGS |
| **Average Order Value** | `SUM([sales])/COUNTD([order_id])` | Customer value (₹51,671) |
| **Return Rate** | `SUM([return_flag])/COUNT([order_id])` | Returns risk signal (4.55%) |
| **Shipping Delay Bucket** | `IF [delivery_days]=0 THEN "Same Day" ELSEIF [delivery_days]<=2 THEN "1-2 Days"...` | Delivery performance grouping |
| **Discount Band** | `IF [discount]=0 THEN "No Discount" ELSEIF [discount]<=0.10 THEN "1-10%"...` | Discount impact analysis |
| **YoY Period** | `STR(YEAR([order_date]))` | Annual comparison |

---

## Dashboard Components

| Component | Chart Type | Business Question |
|-----------|-----------|-------------------|
| Monthly trend | Bar + dual-axis line | How are sales and profit trending? |
| YoY comparison | Grouped bar | Did 2025 outperform 2024? |
| State heatmap | Tile grid | Which states lead in sales and margin? |
| Regional sales | Horizontal bar | Which region has most sales and profit? |
| Region margin table | Metric rows | How do regional margins compare? |
| Sub-category margin | Sorted horizontal bar | Which sub-categories are profitable? |
| Category revenue | Doughnut | What % of revenue per category? |
| Segment comparison | Grouped bar + table | How do segments compare? |
| Discount impact | Bar + line combo | How does discount level hurt margin? |
| Channel performance | Bar + line | Which channel drives best revenue? |
| Ship mode | Bar + line | How do modes compare on volume and speed? |
| Delivery distribution | Doughnut | What % of orders per speed bucket? |
| Return analysis | Horizontal bar | Which categories/segments return most? |

---

## Filters and Interactions

| Filter | Options | Charts Affected |
|--------|---------|----------------|
| Year | All / 2024 / 2025 | Monthly trend |
| Region | All / North / South / East / West | Regional charts |
| Category | All / Technology / Furniture / Office Supplies | Category & sub-cat charts |
| Segment | All / Consumer / Corporate / Home Office | Segment charts |
| Ship Mode | All / four modes | Shipping charts |
| Channel | All / five channels | Channel chart |

All filters update connected charts simultaneously. Filter status indicator + Reset button included.

---

## Key Business Insights

1. Technology = 70.9% of revenue at 18%+ margin — the profit engine
2. Furniture Tables & Bookcases: 5.67–5.71% margin — biggest margin drag
3. Discounts >30% = loss-making (-4.95%) with 64 orders affected
4. South Region leads with ₹6.47Cr sales and ₹99.9L profit
5. Furniture return rate 7.67% — 2.5× Technology's 3.03%
6. Home Office: 5.67% return rate — highest segment risk
7. 288 loss-making orders are concentrated in high-discount Furniture
8. First Class shipping has lowest margin (14.52%) — speed not monetized
9. East Region has highest profit margin (15.55%) despite lower volume
10. April 2025 was worst margin month (12.43%) — requires investigation

---

## Dashboard Story Summary

Technology is driving growth (18%+ margins, 70.9% of revenue). Furniture is the structural drag (6.9% avg margin, 7.67% return rate). The South Region is the geographic growth leader. The single most actionable risk is the discount policy — at 21-30% discounts (the most common order band with 1,086 orders), margin falls to 8.05%, and the 31%+ band actively loses money. A discount cap at 20% would recover approximately ₹1.3Cr in annual profit.

See `outputs/dashboard_story.md` for full leadership narrative.

---

## Assumptions and Limitations

1. `profit` column likely excludes return logistics and some overhead — true margins may be lower
2. 14 rows missing customer_rating, 24 missing campaign_channel — excluded from those analyses
3. 2-year window may not capture full seasonal cycles
4. delivery_days is absolute, not relative to promised date — true late rates uncomputable
5. No competitor pricing data — discount decisions cannot be contextualized against market

---

## Screenshots

| File | Contents |
|------|---------|
| `screenshots/full_dashboard.png` | Complete 7-section executive dashboard |
| `screenshots/sales_trend_view.png` | Monthly sales & profit + margin trend |
| `screenshots/regional_performance_view.png` | State-level and regional charts |
| `screenshots/category_profitability_view.png` | Sub-category margin + category revenue |
| `screenshots/filter_interaction_view.png` | Technology + 2025 filter applied |

---

## File Structure

```
part4/
├── data/dashboard_sales_data.xlsx
├── tableau/
│   ├── executive_dashboard.twbx      ← Tableau packaged workbook
│   └── executive_dashboard.html      ← Interactive HTML (open in browser)
├── outputs/
│   ├── business_insights.md
│   ├── dashboard_story.md
│   └── chart_selection_justification.md
├── screenshots/
│   ├── full_dashboard.png
│   ├── sales_trend_view.png
│   ├── regional_performance_view.png
│   ├── category_profitability_view.png
│   └── filter_interaction_view.png
└── README.md
```
