# CROX: Full Analysis and Partner Questions

Partner company: **GOLF**. The GOLF review record at the end requires the partner's actual analysis and responses before it can be completed.

## 1. Target selection

I selected Crocs (CROX) because it has recognizable brands, substantial cash generation, and a clear business question to investigate: can the core Crocs brand offset weakness in HEYDUDE? Its public financial statements make it suitable for comparing reported profit, cash flow, debt, and valuation. My initial view was **watch/defer**. The business looked worth investigating, but I wanted stronger evidence of sustainable earnings before supporting a purchase.

## 2. Company and evidence

Crocs earns money by selling footwear and accessories through its Crocs and HEYDUDE brands. It sells directly to consumers through stores and online, and through wholesale partners.

The main evidence comes from the saved 2023–2025 annual SEC filings, with a separate historical comparison covering 2021–2025. The filings report financial amounts in thousands of dollars; our model converts them to **millions of dollars**, except per-share figures. Historical results are separate from the 2026–2030 forecasts.

In 2025, revenue fell 1.5% to $4.041 billion. Crocs reported an $81.2 million loss, heavily affected by $738.1 million of asset impairment charges. These charges reduced the recorded value of assets without requiring an equivalent cash payment that year. Crocs still generated $710.4 million in operating cash flow, or $659.2 million after capital expenditures. However, operating cash flow declined from $992.5 million in 2024.

Gross margin fell from 58.76% to 58.33%. Comparable selling, general, and administrative expenses (SG&A) increased from $1.364 billion to $1.469 billion despite lower sales. Year-end debt of approximately $1.231 billion, less $130.4 million of cash, left about $1.101 billion of net debt. Together, these figures make operating costs, HEYDUDE performance, and debt important parts of the analysis.

Evidence: [historical financial statements](CROX-Financial-Statements-2021-2025.md), [saved annual filings](CROX-Proforma-Sources/), and [pro forma report](CROX-Proforma-Report.md). This analysis summarizes the saved evidence; it does not update market data or independently reverify every external claim.

## 3. My pro forma

The pro forma starts with the December 31, 2025 balance sheet and forecasts 2026–2030. I used history to set a starting point, then made explicit judgments about future performance.

| Assumption | Forecast choice | Reason and limitation |
|---|---|---|
| Annual revenue growth | 0%, 1%, 2%, 2.5%, and 2.5% | Assumes a modest recovery after the 2025 decline; this is a judgment, not management guidance. |
| Gross margin | 57.5% each year | Slightly below the 2025 level to allow for cost and product-mix pressure. |
| SG&A | Approximately 62.34% of gross profit | Preserves the 2025 relationship and assumes no improvement in this expense ratio. |
| Capital expenditures | 2% of revenue | Links investment spending to the size of the business. |
| Tax rate | 25% | Uses a normalized assumption because historical effective tax rates were unusual. |
| New impairment charges | Zero | Avoids forecasting an unsupported charge, but materially improves earnings compared with 2025. It does not establish that HEYDUDE has recovered. |
| Debt | Constant balance | Assumes refinancing on similar terms rather than principal repayment; refinancing remains an uncertainty. |

Inventory follows cost of sales, while receivables and other operating balances follow the relevant sales or cost measures. Depreciation and amortization are already included in gross profit and SG&A, so the model does not deduct them a second time when calculating operating profit.

The statements are linked: earnings, noncash expenses, and working-capital movements determine operating cash flow. Capital spending and financing then determine cash available to shareholders. Distributions and earnings also change equity. Positive cash flow to equity is distributed in the base model, while the existing cash buffer is retained.

All five forecast balance sheets balance. Cash and equity movements reconcile, and cash remains above the $100 million floor. The folder's 14 existing tests pass across the CROX, sensitivity, and ABG models. The saved CROX forecast and sensitivity results match recalculation.

Evidence: [model and assumptions](crox_proforma.py), [saved model data](CROX-Proforma-Data.json), and [pro forma report](CROX-Proforma-Report.md).

## 4. Valuation

### Original DCF: $157.74 per share

The original five-year discounted cash-flow model estimated $157.74 per share. It started with $659.2 million of CFO minus capital expenditures, then applied annual growth of 2%, 3%, 4%, 3%, and 2.5%. It used a 10% weighted-average cost of capital (WACC) and 3% perpetual growth after year five, with cash flows discounted at year-end.

The enterprise-to-equity bridge was:

| Item | USD millions, except per-share value |
|---|---:|
| Enterprise value | 9,651.058 |
| Less debt | (1,230.885) |
| Plus cash | 130.354 |
| Equity value | 8,550.527 |
| Annual weighted-average diluted shares, millions | 54.208 |
| Value per share | $157.74 |

This estimate remains provisional. CFO minus capex includes interest effects and needs adjustment before being treated as unlevered free cash flow to the firm (FCFF). The 10% WACC was also a provisional assumption rather than a company-specific calculation.

Evidence: [original DCF script](dcf.py) and [imported discussion](CROX%2010Q%20Summary%20-%20imported.txt).

### Linked pro forma: $122.80 per share

The later model estimated $122.80 per share. It values **free cash flow to equity (FCFE), defined as CFO minus capex plus net borrowing**, using a 12% cost of equity, 2.5% terminal growth, and 50.220 million shares. The share count is a constant year-end basic-share assumption; future dilution is not separately estimated.

Because FCFE already reflects interest and net borrowing, debt is not subtracted again. The model treats opening cash as operating cash and adds no excess cash to the valuation. Approximately 64% of the estimate comes from terminal value, so assumptions about the business beyond 2030 matter substantially.

The two DCF estimates differ because they use different cash-flow definitions, forecast assumptions, discount rates, terminal growth rates, and share counts. Their difference is not simply a market-price update. I put more weight on the linked model because its operating assumptions and accounting relationships are explicit, while recognizing that more detail does not prove those assumptions correct.

The core valuation uses positive forecast FCFE in its price calculation. This does not affect the saved base case because all forecast FCFE is positive. In a scenario with negative FCFE, that convention could omit a cash deficit; the sensitivity script therefore refuses to present a price for such a scenario.

### Market reference and reverse DCF

The pro forma report records a market price of $123.44 at the September 24, 2026 close. The $122.80 estimate is approximately 0.5% below that saved reference price. However, the model is anchored to December 31, 2025 using the subsequently published annual report, so the comparison has a timing limitation and is not a current valuation.

The earlier reverse DCF used $114.35 with an unverified quote date. It held the following inputs fixed:

| Input | Held-fixed value |
|---|---:|
| Starting cash-flow proxy | $659.200 million |
| WACC | 10% |
| Terminal growth | 3% |
| Cash | $130.354 million |
| Debt | $1,230.885 million |
| Shares | 54.208 million |
| Forecast and discount timing | Five years; year-end discounting |

It solved for **−3.5136% annual cash-flow growth for five years**, followed by 3% perpetual growth, to match the $114.35 price. That result describes the growth implied by those inputs. It is not a revenue forecast, and it does not describe the expectations embedded in the separate $123.44 price. The provisional cash-flow definition, WACC, price date, and share basis limit its interpretation.

Evidence: [pro forma valuation and market comparison](CROX-Proforma-Report.md), [reverse DCF report](CROX-Reverse-DCF.md), and [reverse DCF script](reverse_dcf.py).

### Peer comparison

The peer analysis admits Deckers (DECK) and qualifies Steven Madden (SHOO). Both operate footwear businesses, although Deckers has different performance and lifestyle brand exposure, while Steven Madden has broader accessories, apparel, and other business exposure.

The selected peer P/E method uses the latest annual reported GAAP diluted earnings per share available by September 14, 2026. It does not support a CROX target price: matched-date Nasdaq prices remain unresolved, and CROX's negative annual EPS of $1.50 makes applying positive peer P/E multiples economically unhelpful. Quarterly or adjusted earnings would change the chosen method.

DCF values forecast cash flows under explicit assumptions; peer P/E compares market prices with reported earnings. The reverse DCF solves for an implied growth rate at a supplied price. These are different outputs and should not be averaged.

Evidence: [peer comparison](CROX-Peer-Comparison.md) and [peer P/E analysis](peer_pe.md).

## 5. Sensitivity and drivers

Lab 11 changes revenue growth and gross margin one at a time. Every run starts from a fresh copy of the base assumptions, and the full linked model recalculates. All other independent assumptions remain fixed.

| Independent input | Lower | Base | Higher |
|---|---|---|---|
| Annual revenue growth, 2026–2030 | −2%, −1%, 0%, 0.5%, 0.5% | 0%, 1%, 2%, 2.5%, 2.5% | 2%, 3%, 4%, 4.5%, 4.5% |
| Gross margin in every forecast year | 56.0% | 57.5% | 59.0% |

The growth scenarios shift every annual rate by two percentage points below or above base. The margin scenarios shift gross margin by 1.5 percentage points. These are judgment ranges informed by the saved historical results, not probability estimates.

| Scenario | 2030 operating profit, EBIT ($m) | 2030 FCFE ($m) | Value per share |
|---|---:|---:|---:|
| Lower growth | 857.382 | 587.979 | $113.505 |
| Base | 947.001 | 646.471 | $122.795 |
| Higher growth | 1,043.961 | 709.380 | $132.727 |
| Lower gross margin | 922.296 | 627.846 | $119.188 |
| Higher gross margin | 971.705 | 665.097 | $126.402 |

Higher growth compounds revenue over five years. That raises gross profit and operating profit, while taxes, capital expenditures, and working-capital needs absorb some of the additional earnings. Relative to base, the higher-growth case raises 2030 EBIT by $96.960 million, FCFE by $62.909 million, and value by $9.931 per share.

Higher gross margin produces more gross profit at the same sales level. However, SG&A also rises because the model holds it at approximately 62.34% of gross profit. Only about 37.66% of additional gross profit therefore reaches EBIT. Inventory and payables also adjust with cost of sales. Raising margin to 59% increases 2030 EBIT by $24.704 million, FCFE by $18.626 million, and value by $3.607 per share.

Revenue growth produces the larger valuation span: $19.221 per share compared with $7.214 for gross margin. **This ranking applies to these ranges and this model.** Growth has a four-percentage-point lower-to-higher spread in each annual rate and compounds over time; margin has a three-percentage-point spread. Different ranges or expense relationships could change the ranking.

A larger modeled impact does not establish greater uncertainty or a higher probability of change. Assessing uncertainty would require additional evidence about demand, pricing, costs, and the likelihood of different outcomes. The scenarios are conditional calculations, not confidence intervals.

All prescribed cases have positive FCFE and pass the accounting checks. Restoring the base reproduces the original results. Changes and spans use unrounded numbers, so subtracting displayed figures can produce small rounding differences.

Process limitation: the saved submission says its prediction was written after reviewing the results. It is not evidence of a prediction recorded before the run, and the saved Step 1 partner-check fields remain incomplete.

Evidence: [input ranges](CROX-Sensitivity-Step-1.md), [full sensitivity results](CROX-Operating-Sensitivity.md), [audit data](CROX-Operating-Sensitivity-Data.json), and [individual submission](CROX-Sensitivity-Individual-Submission.md).

## 6. Interpretation

My conditional recommendation remains **watch/defer**. Crocs generates substantial cash, but the later model provides little valuation cushion relative to the saved market price. Its estimate depends on modest sales recovery, stable margins, and continued debt refinancing.

My view became more cautious as the work moved from the original $157.74 DCF to the detailed $122.80 estimate. The change shows how much the conclusion depends on the definition of cash flow and the assumptions used to forecast and discount it.

Evidence of HEYDUDE stabilization, controlled overhead, sustainable cash generation, and manageable refinancing would strengthen the case. Further deterioration would weaken it. A lower purchase price could also improve the potential investment case, provided the underlying business outlook had not weakened enough to offset that benefit.

My current decisions are:

- **Keep:** the watch/defer conclusion and the linked statements as the working framework.
- **Revise before relying on the older DCF:** its provisional FCFF proxy and discount-rate basis. Any revision should be recalculated rather than assumed to leave the conclusion unchanged.
- **Investigate next:** the latest quarterly performance by brand, HEYDUDE demand, overhead trends, debt maturities and refinancing terms, and a consistently dated market price and share count.

These priorities focus on whether the model's assumed recovery is supported by evidence. The responses below address the two supplied review questions using the saved analysis. They record my answers, unresolved gaps, and intended next actions; they do not establish that a separate partner evidence check or explanation-back exercise has occurred.

## Partner questions and answers

### Question 1 — Selection, evidence, and valuation

**Question received:**

Why did you select Crocs, and how did the financial evidence lead to your forecast assumptions and $122.80 valuation? Explain why that differs from your original $157.74 estimate, show one supporting source, and identify what you would keep, revise, or investigate next.

**Answer:**

I selected Crocs because it combines recognizable brands and substantial cash generation with a specific concern: whether the Crocs brand can offset weakness in HEYDUDE. That gives me a business question I can connect to financial statements and valuation.

The [saved historical financial statements](CROX-Financial-Statements-2021-2025.md), which link to the annual filings, show that 2025 revenue fell 1.5% to $4.041 billion, gross margin was 58.33%, and comparable SG&A increased despite the sales decline. That evidence led me to assume flat first-year sales followed by modest growth, a slightly lower 57.5% gross margin, and no improvement in SG&A as a percentage of gross profit. These are judgments informed by history, not company guidance. The forecast also assumes no new impairment charges; that removes a major 2025 expense but does not prove that HEYDUDE has recovered.

Those operating assumptions feed into the linked statements and forecast cash available to shareholders. Discounting that FCFE at a 12% cost of equity, with 2.5% terminal growth and 50.220 million shares, produces $122.80 per share. The [pro forma report](CROX-Proforma-Report.md) records the assumptions and result, and the [saved model data](CROX-Proforma-Data.json) preserves the calculations.

The original $157.74 estimate used a different approach: a $659.2 million CFO-minus-capex proxy, a separate cash-flow growth path, 10% WACC, 3% terminal growth, an enterprise-to-equity bridge, and 54.208 million shares. The later model changes several inputs and the valuation basis together. I cannot attribute the full difference to any one assumption without a separate reconciliation. I put more weight on the later model as my working framework because it makes the operating and accounting relationships explicit, while recognizing that its assumptions still need support.

**Specific unresolved gaps:**

- The original cash-flow proxy has not been fully adjusted into unlevered FCFF, and its 10% WACC is provisional. The later 12% cost of equity is also a judgment rather than a separately demonstrated market-based estimate.
- The model's year-end 2025 anchor and the saved September 24, 2026 market price are not aligned. I have not completed an updated valuation using consistently dated information.
- A calculation separating the effects of cash-flow forecasts, discount rates, terminal growth, share count, and other conventions on the valuation difference has not been completed.

**What I will keep, revise, or investigate after this question:**

- **Keep:** the linked model as my working framework and the conditional watch/defer conclusion. Its $122.80 estimate offers little cushion against the saved $123.44 reference price, subject to the timing limitation.
- **Revise:** how I describe the two estimates. I will present $157.74 as a provisional earlier calculation and $122.80 as a conditional linked-model result, without implying that the difference proves a decline in the company's actual value. This document now makes that distinction explicit; the underlying models have not been changed.
- **Investigate:** the cash-flow and discount-rate basis, aligned valuation-date inputs, and the contribution of each assumption to the valuation difference. I will also examine current brand performance and refinancing needs before relying on the forecast recovery.

**Effect on my conclusion and research priority:** The question does not justify a new target price or a stronger recommendation. It makes reconciling the methods and dates a priority before interpreting either estimate as evidence that the stock is cheap.

### Question 2 — Sensitivity, driver ranking, and uncertainty

**Question received:**

Your sensitivity analysis shows revenue growth affects value more than gross margin. Using one scenario, explain how the change flows through profit and cash flow into valuation. How do your chosen ranges affect that ranking, and does a larger impact mean greater uncertainty?

**Answer:**

In the higher-growth scenario, I increased each annual revenue-growth assumption by two percentage points: the base path of 0%, 1%, 2%, 2.5%, and 2.5% became 2%, 3%, 4%, 4.5%, and 4.5%. I held all other independent inputs at base and reran the linked statements.

Higher sales compound over five years and increase gross profit. SG&A also rises because it remains tied to gross profit, while taxes absorb part of the additional earnings. Capital spending stays at 2% of revenue, and receivables, inventory, payables, and other operating balances recalculate with sales or costs. These links determine how much of the profit increase becomes cash flow. In the saved results, 2030 operating profit rises by $96.960 million and FCFE rises by $62.909 million. Discounting the revised cash flows and terminal value raises the share value by $9.931, from approximately $122.80 to $132.73. These changes use unrounded results from the [sensitivity report](CROX-Operating-Sensitivity.md) and [audit data](CROX-Operating-Sensitivity-Data.json).

Across the lower and higher cases, revenue growth produces a $19.221 per-share span, versus $7.214 for gross margin. However, the growth test covers a four-percentage-point spread in each annual growth rate and compounds across five years; the margin test covers a three-percentage-point spread. The model also links SG&A to gross profit, which absorbs much of the gross-margin benefit. The ranking therefore reflects the selected ranges and the model's relationships. It does not establish that growth is always the more important driver.

A larger effect on value measures sensitivity, not uncertainty. It does not tell me whether growth is harder to predict than margin or whether the higher-growth case is likely. Neither these ranges nor the base case has an assigned probability. I would need separate evidence about demand, pricing, product mix, and costs to assess how uncertain the inputs are.

**Specific unresolved gaps:**

- The ranges are historical judgments, not estimated probability distributions. I have not established which input is more uncertain.
- The analysis changes one input at a time. It does not measure a combined outcome such as weak sales occurring alongside lower margins.
- The assumption that SG&A stays at 62.34% of gross profit needs further evaluation because it materially affects the margin sensitivity.
- The saved prediction was written after reviewing results. It cannot support a claim that the outcome was predicted before the scenarios were run.

**What I will keep, revise, or investigate after this question:**

- **Keep:** the saved scenario results and the conclusion that revenue growth has the larger effect over the tested ranges. The statements reconcile, and restoring the base reproduces the initial results.
- **Revise:** the wording of the driver conclusion to state its dependence on the ranges, compounding, and SG&A relationship. I will distinguish sensitivity from likelihood and retain the timing limitation on the prediction. Those explanations are included here; the scenario inputs and results remain unchanged.
- **Investigate:** whether brand-level sales evidence supports the growth range and whether pricing, product mix, and costs support the margin range. I will examine SG&A behavior and consider a separately labeled combined downside scenario after establishing defensible inputs.

**Effect on my conclusion and research priority:** I will prioritize revenue recovery because it has the larger modeled effect in this exercise, while continuing to investigate margins and overhead. This ranking alone does not justify a buy recommendation or establish that revenue is the greatest source of uncertainty. The recommendation remains watch/defer until the operating evidence and valuation assumptions are better supported.

## My review of my partner's company: GOLF

The questions below are prepared; the actual review remains pending until my partner shares their analysis and responses.

### Questions for my partner

1. Why did you select GOLF, how does it earn money, and what evidence supports your initial view?
2. How did history shape your forecast assumptions, and how did you check the linked statements?
3. How do your cash-flow definition, discount rate, terminal assumptions, and debt/share adjustments support your valuation? How do peers and reverse DCF compare?
4. Which sensitivity driver had the largest effect, how did the tested ranges influence that ranking, and what would change your recommendation?
