# Apple Inc. (AAPL) FY2024 – Accounting & Performance Ratio Model: Technical Specification

**Created by:** Mia Fong
**Updated by:** Mia Fong
**Date Created:** 2025
**Date Updated:** 2025
**Version:** 1.1
**LLM Used:** Claude (Anthropic) — used to assist with data extraction and draft refinement

**Role:** Financial Analyst / FP&A Analyst
**Audience:** CFO or Director of FP&A

**Purpose:** This specification documents the analytical structure of a quantitative Excel model that computes 25+ accounting and performance ratios from Apple Inc.'s FY2024 financial statements. It serves simultaneously as a post-build audit record and a forward-looking blueprint for a refined model in Stage 4.

---

## 1. Problem Statement

Apple Inc. (AAPL) is a publicly traded technology company operating in consumer electronics, software, and services. This specification documents the analytical framework for computing 25+ accounting and performance ratios from Apple's FY2024 10-K filing (fiscal year ending September 28, 2024), with FY2023 (September 30, 2023) serving as the prior-year comparative period.

The objective is to assess Apple's financial health across five dimensions — performance, profitability, operational efficiency, leverage, and liquidity — and to quantify value creation through MVA, EVA, and Du Pont decomposition. All figures are reported in millions of US dollars. This analysis is intended for a CFO briefing and as the direct input to a Stage 4 AI-assisted executive memo.

---

## 2. Inputs (Known Variables)

All figures in $millions unless otherwise noted.

### Balance Sheet Items

| Variable | Description | Named Range | FY2024 | FY2023 |
|---|---|---|---|---|
| Cash & marketable securities | Liquid assets | `BAL_cash_marketable_securities_[year]` | 65,171 | 61,555 |
| Receivables | Accounts receivable | `BAL_receivables_[year]` | 33,410 | 29,508 |
| Inventories | Inventory balance | `BAL_inventories_[year]` | 7,286 | 6,331 |
| Total current assets | Sum of current assets | `BAL_assets_current_[year]` | 152,987 | 143,566 |
| Net tangible fixed assets | PP&E net of accumulated depreciation | `BAL_fixed_assets_net_[year]` | 45,680 | 43,715 |
| Total assets | All assets | `BAL_assets_total_[year]` | 364,980 | 352,583 |
| Total current liabilities | Short-term obligations | `BAL_liabilities_current_[year]` | 176,392 | 145,308 |
| Long-term debt | Non-current borrowings | `BAL_debt_long_term_[year]` | 85,750 | 95,281 |
| Total liabilities | All liabilities | `BAL_liabilities_total_[year]` | 308,030 | 290,437 |
| Shareholders' equity | Book value of equity | `BAL_equity_shareholders_[year]` | 56,950 | 62,146 |

### Income Statement Items

| Variable | Description | Named Range | FY2024 |
|---|---|---|---|
| Net sales | Total revenue | `INC_sales` | 391,035 |
| Cost of goods sold | Direct costs | `INC_cost_goods_sold` | 210,352 |
| SG&A expenses | Operating expenses | `INC_sga` | 26,097 |
| Depreciation | Non-cash charge | `INC_depreciation` | 11,445 |
| EBIT | Operating income | `INC_ebit` | 143,141 |
| Other income | Non-operating income | `INC_other_income` | 3,764 |
| Interest expense | Cost of debt | `INC_interest_expense` | 3,931 |
| Taxes | Income tax expense | `INC_taxes` | 29,749 |
| Net income | Bottom line | `INC_net` | 113,225 |
| Dividends | Shareholder distributions | `INC_dividends` | 15,234 |

### Cash Flow Statement Items

| Variable | Description | Named Range | FY2024 |
|---|---|---|---|
| Cash from operations | Operating cash flow | `CASH_operating` | 148,859 |
| Cash from investments | Investing cash flow | `CASH_investments` | 2,935 |
| Cash from financing | Financing cash flow | `CASH_financing` | -121,983 |

### Market / Analyst Inputs

| Variable | Description | Named Range | Value |
|---|---|---|---|
| Share price | End-of-fiscal-year closing price | `share_price` | $226.51 |
| Shares outstanding | Total shares (millions) | `shares_outstanding` | 15,204 |
| Cost of capital | Estimated WACC | `cost_capital` | 9.0% |
| Tax rate | Effective tax rate (FY2024) | `tax_rate` | 24.1% |

---

## 3. Assumptions & Constraints

- All figures reported in millions of US dollars unless otherwise noted.
- Tax rate set at 24.1%, reflecting Apple's effective rate from the FY2024 10-K; analysts may substitute the statutory 21% for cross-company comparisons.
- Cost of capital estimated at 9.0% (approximate WACC); may be refined using CAPM plus capital structure weighting.
- Share price represents the closing market price on the fiscal year-end date (September 28, 2024).
- Depreciation figure sourced from the Income Statement; consistent with the Cash Flow Statement addback.
- Start-of-year balance sheet values use FY2023 ending balances throughout.
- Total capitalization defined as long-term debt plus shareholders' equity; excludes operating lease obligations and off-balance-sheet items.
- No off-balance-sheet items, contingent liabilities, or non-controlling interests are included.
- Interest rates treated on a simple annual basis; no compounding adjustments applied.
- Apple's retained earnings are negative (accumulated deficit due to share buybacks); this is correctly reflected in the equity figure.

---

## 4. Calculation Flow

### Step 1: Market & Derived Inputs

1. `market_capitalization` = `share_price` × `shares_outstanding`
2. `currentYear_after_tax_operating_income` = `INC_net` + (1 − `tax_rate`) × `INC_interest_expense`
3. `currentYear_daily_sales_average` = `INC_sales` / 365
4. `currentYear_cost_goods_sold_daily` = `INC_cost_goods_sold` / 365
5. `currentYear_working_capital_net` = `BAL_assets_current_2024` − `BAL_liabilities_current_2024`
6. `currentYear_total_capitalization` = `BAL_debt_long_term_2024` + `BAL_equity_shareholders_2024`
7. `startYear_total_capitalization` = `BAL_debt_long_term_2023` + `BAL_equity_shareholders_2023`
8. Averages: `avg_equity`, `avg_total_assets`, `avg_total_capitalization` = AVERAGE(start, current) for each

### Step 2: Performance Ratios

- **MVA** = `market_capitalization` − `currentYear_equity`
- **Market-to-Book** = `market_capitalization` / `currentYear_equity`
- **EVA** = `currentYear_after_tax_operating_income` − (`cost_capital` × `startYear_total_capitalization`)

### Step 3: Profitability Ratios

- **ROA** = `currentYear_after_tax_operating_income` / `startYear_total_assets`
- **ROC** = `currentYear_after_tax_operating_income` / `startYear_total_capitalization`
- **ROE** = `INC_net` / `startYear_equity`
- Repeat each using average denominators (`avg_total_assets`, `avg_total_capitalization`, `avg_equity`)

### Step 4: Efficiency Ratios

- **Asset Turnover** = `INC_sales` / `startYear_total_assets`
- **Receivables Turnover** = `INC_sales` / `startYear_receivables`
- **Average Collection Period** = `startYear_receivables` / `currentYear_daily_sales_average`
- **Inventory Turnover** = `INC_cost_goods_sold` / `startYear_inventory`
- **Days in Inventory** = `startYear_inventory` / `currentYear_cost_goods_sold_daily`
- **Profit Margin** = `INC_net` / `INC_sales`
- **Operating Profit Margin** = `currentYear_after_tax_operating_income` / `INC_sales`

### Step 5: Leverage Ratios

- **Long-term Debt Ratio** = `currentYear_debt_long_term` / (`currentYear_debt_long_term` + `currentYear_equity`)
- **Long-term Debt-to-Equity** = `currentYear_debt_long_term` / `currentYear_equity`
- **Total Debt Ratio** = `currentYear_liabilities_total` / `currentYear_assets_total`
- **Times Interest Earned** = `INC_ebit` / `INC_interest_expense`
- **Cash Coverage** = (`INC_ebit` + `INC_depreciation`) / `INC_interest_expense`
- **Debt Burden** = `INC_net` / `currentYear_after_tax_operating_income`
- **Leverage Ratio** = `currentYear_assets_total` / `currentYear_equity`

### Step 6: Liquidity Ratios

- **NWC-to-Assets** = `currentYear_working_capital_net` / `currentYear_assets_total`
- **Current Ratio** = `currentYear_assets_current` / `currentYear_liabilities_current`
- **Quick Ratio** = (`currentYear_cash_marketable_securities` + `BAL_receivables_2024`) / `currentYear_liabilities_current` *(resolved from prior placeholder `BAL_receivables_YEAR`)*
- **Cash Ratio** = `currentYear_cash_marketable_securities` / `currentYear_liabilities_current`

### Step 7: Du Pont Decomposition

- **Du Pont ROA** = `RATIO_asset_turnover` × `RATIO_operating_profit_margin`
- **Du Pont ROE** = `RATIO_leverage` × `RATIO_asset_turnover` × `RATIO_operating_profit_margin` × `RATIO_debt_burden`

Named-range aliases (`RATIO_asset_turnover`, `RATIO_operating_profit_margin`, `RATIO_leverage`, `RATIO_debt_burden`) are assigned in their respective sections — Efficiency and Leverage — and referenced directly by the Du Pont block. This avoids re-entering raw inputs and keeps the decomposition automatically consistent with the ratio table above it. Du Pont ROA resolves to 0.3296 (matching the direct ROA calculation to four decimal places); Du Pont ROE resolves to 2.058.

---

## 5. Outputs

| Output | Description | Format | Purpose |
|---|---|---|---|
| Ratio summary table | 25+ ratios organized by category (Performance, Profitability, Efficiency, Leverage, Liquidity) | Table | Core analytical deliverable |
| Du Pont decomposition | ROA and ROE broken into component drivers | Table | Identifies primary return levers |
| Named-range formula column | Pseudocode formula alongside each ratio result | Column | Auditability and reproducibility |
| Common-size income statement | Each income line as % of net sales | Column | Quick margin benchmarking |
| Notes & Assumptions tab | All analyst inputs, data sources, and conventions | Worksheet | Documentation and transparency |

---

## 6. Model Review — What Worked & What to Improve

**What worked well:**
The named-range architecture is the model's primary strength. Every ratio formula references descriptive range names (e.g., `INC_net / startYear_equity`) rather than cell addresses, making formulas self-documenting and audit-friendly. The color coding — blue for analyst assumptions, green for financial statement inputs, yellow for computed outputs — creates clear visual separation of data types. The balance sheet check (Total Assets − Total Liabilities & Equity = 0) confirmed data entry accuracy. The cash flow statement was constructed from scratch using balance sheet changes, providing a useful cross-check against reported figures.

The Du Pont decomposition is correctly implemented in the current version. Named-range aliases (`RATIO_asset_turnover`, `RATIO_operating_profit_margin`, `RATIO_leverage`, `RATIO_debt_burden`) are assigned at their source rows in the Efficiency and Leverage sections, respectively, and the Du Pont block references them directly. Du Pont ROA (0.3296) matches the direct ROA calculation to four decimal places, confirming internal consistency. Du Pont ROE (2.058) is consistent with the leverage, margin, and burden components.

The Quick Ratio formula has been fully resolved: the prior `BAL_receivables_YEAR` placeholder has been replaced with `BAL_receivables_2024`, eliminating the undefined-range risk and correcting the output to 0.5589.

**What should be improved:**
The `RATIO_*` namespace is currently doing double duty — it serves as both a ratio output label and a Du Pont input alias. While this works in the current single-year model, it would become fragile in a multi-year or multi-company version. A future build should separate these into distinct namespaces (e.g., `DUPONT_asset_turnover`) to avoid aliasing conflicts.

Finally, the model would benefit from a dedicated "Sensitivity" tab allowing the cost of capital and tax rate to be varied across a range of scenarios, given how materially EVA and after-tax operating income respond to those two inputs. A one-way data table on `cost_capital` vs. EVA would take minutes to build and add meaningful analytical depth for a CFO presentation.

---

## 7. Limitations & Next Steps

This model covers a single fiscal year (FY2024) against one prior-year comparison (FY2023) and does not incorporate multi-year trend analysis, industry peer benchmarks, or segment-level data. Off-balance-sheet items, operating lease obligations, and non-GAAP adjustments disclosed in Apple's 10-K are excluded. The cost of capital is an analyst estimate and has not been formally derived from CAPM or a capital structure model.

The next phase (Stage 4) will involve submitting a structured AI prompt — built directly from this specification's Calculation Flow and Model Review sections — to produce a polished, sensitivity-enabled model and an executive memo interpreting the ratio results and providing strategic recommendations to senior management.
