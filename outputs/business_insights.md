# Business Insights
## Retail Executive Dashboard — 2024–2025

### Calculated Fields
| Field | Formula | Purpose |
|-------|---------|---------|
| Profit Margin | `SUM([profit]) / SUM([sales])` | Core profitability KPI |
| Cost | `[sales] - [profit]` | Estimated COGS |
| Average Order Value | `SUM([sales]) / COUNTD([order_id])` | Customer value signal (₹51,671) |
| Return Rate | `SUM([return_flag]) / COUNT([order_id])` | Returns risk (4.55% overall) |
| Shipping Delay Bucket | `IF [delivery_days]=0 THEN "Same Day" ELSEIF ≤2 THEN "1-2 Days"...` | Delivery segmentation |
| Discount Band | `IF [discount]=0 THEN "No Discount" ELSEIF ≤0.10 THEN "1-10%"...` | Discount impact analysis |
| YoY Period | `STR(YEAR([order_date]))` | Annual comparison |

---

## Insight 1 — Sales Trend: Mid-Year Trough in 2024, Recovery in 2025 H2

**Observation:** August 2024 was the weakest month (₹63L, 149 orders). 2025 H2 bounced strongly: July–August 2025 averaged ₹107L/month.

**Evidence:** 2024 total ₹10.62Cr; 2025 total ₹11.08Cr (+4.3% YoY). April 2025 had the lowest margin (12.43%); December 2024 the highest (17.51%).

**Business interpretation:** The 2024 mid-year slowdown did not repeat in 2025, suggesting demand stimulation or new product lines drove H2 recovery. Margin volatility (12.43%–17.51%) indicates inconsistent pricing discipline.

**Recommended action:** Investigate what drove the 2025 H2 surge and replicate those strategies in the historically weak May–August window. Implement margin floor alerts for months trending below 14%.

---

## Insight 2 — Regional Performance: South Leads Volume, East Leads Margin

**Observation:** South Region generates the most revenue (₹6.47Cr, 1,210 orders) but East Region has the highest profit margin (15.55%).

**Evidence:** South: ₹9.99M profit, 15.44% margin. East: ₹7.60M profit, 15.55% margin. Jharkhand (East) is the highest-margin state at 16.83%.

**Business interpretation:** South's scale advantage comes without margin sacrifice — it is the growth frontier. East's superior margins despite lower volume suggest better pricing discipline or product mix.

**Recommended action:** Invest in Technology product expansion in East states (Jharkhand, Assam) to capture high-margin growth. Use East's pricing model as a template for South market expansion.

---

## Insight 3 — Category: Technology Is the Profit Engine, Furniture Is the Drag

**Observation:** Technology contributes 70.9% of revenue (₹15.4Cr) at 18%+ margins. Furniture contributes 23.8% at only 5.67–8.25% margins.

**Evidence:** Technology avg margin: 18.2%. Furniture avg margin: 6.9%. Office Supplies: 14.9%. Furniture generates ₹5.16Cr in sales but only ₹35.6L in profit vs Technology's ₹28.0M.

**Business interpretation:** Furniture is consuming shelf space, logistics, and return costs with inadequate margin return. It dilutes the overall blended margin from what could be ~18% to 15.35%.

**Recommended action:** Review Furniture pricing — minimum 12% target margin. Evaluate whether Tables (5.67%) and Bookcases (5.71%) justify continued stocking at current price points.

---

## Insight 4 — Sub-Category: Bookcases & Tables Are Double Risks (Low Margin + High Returns)

**Observation:** Tables (5.67% margin, 6.16% return rate) and Bookcases (5.71% margin, 8.42% return rate) are the portfolio's two weakest performers on both dimensions simultaneously.

**Evidence:** Bookcases: ₹1.25Cr sales, 24 returns of 285 orders. Tables: ₹1.29Cr sales, 18 returns of 292 orders. Both below 10% margin — the lowest in the entire portfolio.

**Business interpretation:** Every Bookcase return is particularly damaging: the item was already marginally profitable at best, and return logistics cost erases remaining contribution.

**Recommended action:** Implement "exchange-only" policy for Bookcases and Tables. Audit product descriptions to reduce mismatch-driven returns. Consider a 15% price increase experiment on both sub-categories.

---

## Insight 5 — Customer Segments: Home Office Is Most Valuable But Highest Return Risk

**Observation:** Home Office leads in revenue (₹7.45Cr) and profit (₹1.16Cr) but carries a 5.67% return rate — 1.45× the Consumer segment (3.91%).

**Evidence:** Home Office: 1,446 orders, 82 returns. Consumer: 1,355 orders, 53 returns. Margins are similar across all three segments (15.18%–15.51%).

**Business interpretation:** Home Office buyers are generating the highest revenue but also the most operational friction. If the return rate crosses 7%, this segment becomes a net liability.

**Recommended action:** Add pre-purchase comparison tools for Home Office buyers. Implement a post-purchase satisfaction survey at day 7 to catch issues before they become returns.

---

## Insight 6 — Discount Impact: Every 10% More Discount = ~5pp Margin Loss

**Observation:** Profit margin collapses linearly with discount: No discount = 20.56%, 1-10% = 17.01%, 11-20% = 13.63%, 21-30% = 8.05%, 31%+ = -4.95%.

**Evidence:** 64 orders at 31%+ discount generated -₹1.02L in losses on ₹20.7L of sales. The 21-30% band is the largest by order count (1,086 orders).

**Business interpretation:** The 21-30% discount band has more orders than any other — meaning the company's most common discount level is also one of the most margin-damaging. This is not promotional strategy, it is systemic value destruction.

**Recommended action:** Cap standard discounts at 20%. Require senior sign-off for any discount above 20%. Build profitability guardrails into the order management system.

---

## Insight 7 — Shipping: Standard Class Has the Best Margin; First Class Underperforms

**Observation:** Standard Class (4.71 avg days) delivers the highest margin (15.54%) among all ship modes. First Class (1.77 avg days) has the lowest margin (14.52%).

**Evidence:** First Class: 630 orders, ₹3.19Cr sales, ₹46.4L profit (14.52%). Standard Class: 2,435 orders, ₹12.28Cr sales, ₹1.91Cr profit (15.54%).

**Business interpretation:** The speed premium of First Class is not being passed through in pricing. Customers get faster delivery at a cost the business absorbs rather than charges.

**Recommended action:** Increase First Class surcharges by 8-10% or renegotiate courier contracts. Test whether First Class customers are price-sensitive to a moderate surcharge increase.

---

## Insight 8 — Return Patterns: Furniture Return Rate Is a Structural Risk

**Observation:** Furniture has a 7.67% return rate — 2.5× Technology (3.03%) and 2.1× Office Supplies (3.65%).

**Evidence:** 88 Furniture returns of 1,147 orders. Sub-category breakdown: Bookcases 8.42%, Furnishings 8.16%, Chairs 7.99%, Tables 6.16%.

**Business interpretation:** Furniture's combined problem — lowest margins + highest returns — makes it the category most at risk of being net-negative when return logistics are included. At current scale, reverse logistics for 88 returns annually represents meaningful untracked cost.

**Recommended action:** Quantify actual return processing cost per order. If Furniture reverse logistics cost exceeds ₹2,000/order, the category's true profitability is materially worse than the dashboard shows.

---

## Insight 9 — Campaign Channel: Organic Dominates Volume; Referral Has Highest Return Risk

**Observation:** Organic drives 40% of orders (1,694) at competitive margins. Referral channel has the highest return rate (5.61%) of all acquisition channels.

**Evidence:** Organic: ₹8.88Cr sales, 15.14% margin, 4.43% return rate. Referral: ₹2.12Cr, 15.73% margin, 5.61% return rate. Social: lowest return rate (3.94%).

**Business interpretation:** Referral customers arrive with higher expectations (set by the referring customer's experience) and return more. Social-acquired customers have the best retention behavior.

**Recommended action:** Audit referral program messaging for product accuracy. Expand Social channel investment — it combines acceptable volume with the best return quality.

---

## Insight 10 — Business Risk: 288 Loss-Making Orders Are a Structural Profitability Leak

**Observation:** 288 orders (6.9%) generated negative profit — concentrated in high-discount Furniture transactions.

**Evidence:** 64 orders with 31%+ discounts = -₹1.02L. Loss-making orders appear disproportionately in Furniture Tables and Bookcases with discounts above 20%.

**Business interpretation:** This is not random — high-discount + low-margin category = guaranteed losses. It is addressable with policy changes, not market changes.

**Recommended action:** Block discount rates above 15% for Furniture sub-categories system-wide. Build an order-level profitability predictor that alerts sales teams before they submit a loss-making order.
