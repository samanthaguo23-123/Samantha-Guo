# Stage 5 — FX Hedging Validation Analysis

**Scenario:** 15 — Landing Gear  
**Date:** November 27, 2026  
**Market data date:** November 19, 2026  
**Exposure:** EUR 10,500,000 receivable  
**Settlement period:** 365 days  
**Reporting currency:** USD

## 1. Independent LLM Execution

The objective of this validation was to determine whether the Stage 2 specification and Stage 4 market-data memo contained sufficient information for an independent LLM to reproduce the FX hedging model.

I opened a fresh LLM conversation and provided exactly two documents:

- [Stage 2 — FX Hedging Specification](../capabilities/fx-hedging/spec.md)
- [Stage 4 — Market Data Memo](../data/2026-11-19-landing-gear-market-data-memo.md)

The Excel workbook was not provided separately, and no corrections or additional guidance were given during the independent execution.

### Original Prompt

Using only the two provided documents, independently compute all hedge outcomes for the specified foreign exchange exposure, including the forward hedge, money-market hedge, put option, call option, and unhedged position.

Show your calculations, assumptions, and sensitivity analysis at multiple settlement exchange rates. Evaluate covered interest parity and recommend a hedging strategy to the CFO based on your results.

Identify any missing information or ambiguities in the provided documents and disclose any assumptions you make.

### Raw LLM Output

The complete original response is preserved in the following file:

[Independent LLM Output](2026-11-27-landing-gear-independent-llm-output.md)

### Independence Limitation

The Stage 4 market-data memo already contained several workbook cross-check results. Therefore, agreement with those figures alone does not establish independent mathematical accuracy. Additional hand verification is necessary.

## 2. Comparison Against Excel Workbook

The independent LLM results were compared against the saved outputs in the Excel workbook at three settlement exchange rates: 5% EUR depreciation, unchanged spot, and 5% EUR appreciation.

[Excel Hedging Model](../capabilities/fx-hedging/model.xlsx)

All monetary amounts are expressed in USD.

| Settlement Rate | Strategy | LLM Result | Workbook Result | Difference | Status |
|---|---|---:|---:|---:|---|
| 1.044240 (-5%) | Forward | 12,397,350.00 | 12,397,350.00 | 0.00 | PASS |
| 1.044240 (-5%) | Money-market | 11,721,307.56 | 11,721,307.56 | 0.00 | PASS |
| 1.044240 (-5%) | Put | 11,272,299.98 | 11,272,299.98 | 0.00 | PASS |
| 1.044240 (-5%) | Unhedged | 10,964,520.00 | 10,964,520.00 | 0.00 | PASS |
| 1.099200 (0%) | Forward | 12,397,350.00 | 12,397,350.00 | 0.00 | PASS |
| 1.099200 (0%) | Money-market | 11,721,307.56 | 11,721,307.56 | 0.00 | PASS |
| 1.099200 (0%) | Put | 11,272,299.98 | 11,272,299.98 | 0.00 | PASS |
| 1.099200 (0%) | Unhedged | 11,541,600.00 | 11,541,600.00 | 0.00 | PASS |
| 1.154160 (+5%) | Forward | 12,397,350.00 | 12,397,350.00 | 0.00 | PASS |
| 1.154160 (+5%) | Money-market | 11,721,307.56 | 11,721,307.56 | 0.00 | PASS |
| 1.154160 (+5%) | Put | 11,849,379.98 | 11,849,379.98 | 0.00 | PASS |
| 1.154160 (+5%) | Unhedged | 12,118,680.00 | 12,118,680.00 | 0.00 | PASS |

### 2.1 Call Option Comparison

The EUR call option is evaluated separately because it protects a EUR payable rather than a EUR receivable.

| Settlement Rate | Call Calculation | LLM Result | Workbook Result | Status |
|---|---|---:|---:|---|
| 1.044240 (-5%) | Standalone net payoff | -492,434.32 | Not displayed | Pending |
| 1.044240 (-5%) | Payable outlay | 11,456,954.32 | Not displayed | Pending |
| 1.099200 (0%) | Standalone net payoff | -492,434.32 | -492,434.32 | PASS |
| 1.099200 (0%) | Payable outlay | 12,034,034.32 | 12,034,034.32 | PASS |
| 1.154160 (+5%) | Standalone net payoff | 84,645.68 | Not displayed | Pending |
| 1.154160 (+5%) | Payable outlay | 12,034,034.32 | Not displayed | Pending |

### 2.2 Preliminary Discrepancy Diagnosis

All directly comparable numerical results agree to the nearest cent.

The workbook does not display call option sensitivity outcomes at the -5% and +5% settlement rates because its sensitivity table focuses on strategies relevant to the EUR receivable. This is a comparison coverage limitation rather than an established calculation error.

The remaining call outcomes will be checked separately.

### 2.3 Covered Interest Parity

| Measurement | LLM Result | Workbook Result |
|---|---:|---:|
| Assigned forward rate | 1.180700 | 1.180700 |
| CIP-implied forward rate | 1.116315 | 1.116315 |
| Rate difference (CIP minus assigned) | -0.064385 | -0.064385 |
| Absolute percentage difference | 5.4531% | 5.4531% |
| Parity status | REVIEW | REVIEW |

The parity discrepancy reflects the inconsistency between the assigned forward quote and the theoretical forward rate implied by the supplied market inputs. It is not, by itself, evidence of a formula error.

Independent hand verification will be performed before reaching a final validation conclusion.
