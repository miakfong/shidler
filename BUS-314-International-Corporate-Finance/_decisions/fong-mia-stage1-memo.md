# Accounting Ratio Analysis — Apple Inc. (AAPL): Project Scope & Rationale

**Created by:** Mia Fong
**Updated by:** Mia Fong
**Date Created:** April 2, 2026
**Date Updated:** April 3, 2026
**Version:** 1.1
**LLM Used:** Claude Sonnet 4.6

---

## Executive Summary (150 words max)

This memo frames a comprehensive accounting ratio analysis of Apple Inc. (AAPL) for fiscal year 2024 (ended September 28, 2024). Apple is the world's largest consumer technology company by market capitalization, generating $391 billion in net sales across hardware, software, and services. While Apple's raw financial statements confirm its scale, they do not readily reveal how efficiently the company deploys assets, how comfortably it services debt, or how profitability has evolved year over year. This project will compute ratios across six categories — Performance, Profitability, Efficiency, Leverage, Liquidity, and Du Pont — using data sourced from Apple's FY2024 10-K filing with the SEC. The analysis will deliver a working Excel model (Stage 2), a technical specification (Stage 3), and a final strategic interpretation memo (Stage 4), providing leadership with a structured, data-driven view of Apple's financial health.

---

## Company Background & Objectives

**Company:** Apple Inc. (NASDAQ: AAPL)
**Industry:** Technology — Consumer Electronics & Software
**Business:** Apple designs, manufactures, and markets smartphones, personal computers, tablets, wearables, and a growing suite of digital services including the App Store, Apple Music, iCloud, and Apple TV+.

The fiscal year under review is FY2024, covering the twelve months ended September 28, 2024, with FY2023 (ended September 30, 2023) serving as the prior-year comparison period. All financial figures are denominated in millions of U.S. dollars as reported in Apple's annual 10-K filing with the SEC.

A comprehensive ratio analysis is valuable here for several reasons. Apple operates at an unusual intersection of hardware margins, high-margin services growth, and aggressive capital return programs — including $94.9 billion in share repurchases in FY2024 alone. These dynamics create patterns that raw income statement or balance sheet figures can obscure. Ratio analysis cuts through the scale of the numbers to reveal relative performance: whether Apple is becoming more or less efficient at turning assets into revenue, how its leverage profile is shifting as long-term debt stands at $85.8 billion, and whether its liquidity position is sufficient relative to $129.9 billion in current liabilities. The CFO and senior leadership can use these insights to benchmark Apple against industry peers, evaluate capital allocation decisions, and identify areas warranting closer scrutiny before the next earnings cycle.

---

## Approach

This analysis will draw exclusively on Apple's FY2024 Annual Report (Form 10-K) filed with the U.S. Securities and Exchange Commission via SEC EDGAR, supplemented by the structured scenario workbook prepared for BUS 314. The workbook consolidates Apple's Balance Sheet, Income Statement, and Cash Flow Statement into a single model with named ranges that feed directly into ratio formulas.

Six ratio categories will be computed and interpreted:

1. **Performance** — Measures top-line and bottom-line scale relative to equity and assets; includes return on assets and return on equity.
2. **Profitability** — Evaluates margin efficiency at various points on the income statement (gross, operating, net, and EBIT margins).
3. **Efficiency** — Assesses how productively Apple converts assets, inventory, and receivables into sales; includes asset turnover, inventory days, and days sales outstanding.
4. **Leverage** — Quantifies Apple's reliance on debt financing relative to equity and total assets; includes long-term debt ratio, total debt ratio, times interest earned, and cash coverage.
5. **Liquidity** — Examines Apple's ability to meet near-term obligations; includes current ratio, quick ratio, and cash ratio.
6. **Du Pont System** — Decomposes return on equity into its component drivers — leverage, asset turnover, operating margin, and debt burden — to identify the precise sources of shareholder returns.

Results will be organized in a structured Excel model using named ranges for auditability and ease of update. All ratio outputs will be clearly labeled with formula logic documented for review.

---

## Limitations & Next Steps

**Known Limitations:**
- The analysis covers a single fiscal year (FY2024) with one prior-year comparison (FY2023). Multi-year trend analysis and peer benchmarking are outside the scope of this stage.
- Apple's fiscal year ends in late September, which may affect seasonality comparisons with calendar-year peers.
- The share price used for market-based ratios ($226.51) reflects the end-of-fiscal-year closing price and may not represent current market conditions.
- The effective tax rate applied (24.1%) is an analyst assumption and may differ slightly from Apple's reported rate in other filings.
- Apple carries zero goodwill on its balance sheet as reported, which limits intangible asset analysis.

**Immediate Next Steps:**

- **Stage 2:** Build the working Excel model by entering all ratio formulas into the Ratios tab using the provided named ranges. Verify formula outputs against manually calculated spot checks.
- **Stage 3:** Produce a technical specification documenting the model's structure, formula logic, named range conventions, color-coding, and lessons learned during the build process.
- **Stage 4:** Write a final executive memo interpreting the ratio results, identifying strategic implications, and formulating recommendations for leadership. A structured AI prompt will also be developed and documented.

---

## References

Apple Inc. (2024). *Annual Report on Form 10-K for the fiscal year ended September 28, 2024*. U.S. Securities and Exchange Commission, EDGAR Filing. https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=AAPL&type=10-K

Brealey, R. A., Myers, S. C., & Allen, F. (2023). *Principles of Corporate Finance* (14th ed.). McGraw-Hill Education.

Stauffer, A. (2026). *BUS314_AAPL_Scenario.xlsx* — Apple Inc. scenario workbook. University of Hawaiʻi at Mānoa, Shidler College of Business.
