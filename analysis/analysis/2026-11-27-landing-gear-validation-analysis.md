### 2.1 Call Option Comparison

The EUR call option is evaluated separately because it protects a EUR payable rather than a EUR receivable.

To verify the call option sensitivity outcomes, I temporarily adjusted the settlement exchange rate in cell B22 of the Inputs worksheet and reviewed the calculated results in cells B16 and B17 of the Option_Hedge worksheet.

| Settlement Rate | Call Calculation | LLM Result | Workbook Result | Difference | Status |
|---|---|---:|---:|---:|---|
| 1.044240 (-5%) | Standalone net payoff | -492,434.32 | -492,434.32 | 0.00 | PASS |
| 1.044240 (-5%) | Payable outlay | 11,456,954.32 | 11,456,954.32 | 0.00 | PASS |
| 1.099200 (0%) | Standalone net payoff | -492,434.32 | -492,434.32 | 0.00 | PASS |
| 1.099200 (0%) | Payable outlay | 12,034,034.32 | 12,034,034.32 | 0.00 | PASS |
| 1.154160 (+5%) | Standalone net payoff | 84,645.68 | 84,645.68 | 0.00 | PASS |
| 1.154160 (+5%) | Payable outlay | 12,034,034.32 | 12,034,034.32 | 0.00 | PASS |

After completing the sensitivity tests, I restored the original baseline formula, `=S0_in`, in cell B22.

### 2.2 Discrepancy Diagnosis

All 18 compared outcomes agree between the independent LLM response and the Excel workbook to the nearest cent.

The initial comparison limitation arose because the workbook's sensitivity table focuses on strategies relevant to the EUR receivable and does not display call option outcomes at every settlement rate.

This limitation was resolved by temporarily adjusting the settlement exchange rate and observing the existing call option formulas.

Although no numerical discrepancies were identified between the two sets of reported results, agreement does not independently establish mathematical correctness. Both could contain the same calculation error. Therefore, hand verification remains necessary.

**Comparison status: PASS — All 18 outcomes match, subject to independent arithmetic verification.**

## 3. Independent Hand Verification

To verify the mathematical accuracy of the Excel workbook and the independent LLM response, I manually recalculated three hedge strategies using a calculator rather than Excel. I used the named-range inputs from the populated model and retained full numerical precision between calculation steps.

### 3.1 Input Values

| Named Range | Value |
|---|---:|
| FC_AMT | EUR 10,500,000 |
| S0_in | 1.0992 |
| F0_in | 1.1807 |
| R_USD | 0.0462 |
| R_FC | 0.03037 |
| T_DAYS | 365 |
| BASIS | 360 |
| K_PUT | 1.0992 |
| PREM_PUT | 0.0245 |

### 3.2 Hand-Verification Table

| Calculation | Named-Range Formula | Arithmetic | Hand Result |
|---|---|---|---:|
| Forward proceeds | FC_AMT × F0_in | 10,500,000 × 1.1807 | $12,397,350.00 |
| MM Step 1: EUR borrowed | FC_AMT / (1 + R_FC × T_DAYS / BASIS) | 10,500,000 / (1 + 0.03037 × 365 / 360) | €10,186,344.07 |
| MM Step 2: USD converted | BORROW_EUR × S0_in | 10,186,344.073952857 × 1.0992 | $11,196,829.41 |
| MM Step 3: USD invested | USD_NOW × (1 + R_USD × T_DAYS / BASIS) | 11,196,829.40608898 × (1 + 0.0462 × 365 / 360) | $11,721,307.56 |
| Initial put premium | FC_AMT × PREM_PUT | 10,500,000 × 0.0245 | $257,250.00 |
| Financed put premium | FC_AMT × PREM_PUT × (1 + R_USD × T_DAYS / BASIS) | 257,250 × (1 + 0.0462 × 365 / 360) | $269,300.02 |
| Put net proceeds at -5% | FC_AMT × MAX(S_T, K_PUT) − financed premium | 10,500,000 × MAX(1.044240, 1.0992) − 269,300.01875 | $11,272,299.98 |

### 3.3 Reconciliation of Hand Calculations

| Calculation | Hand Result | Excel Result | LLM Result | Difference | Status |
|---|---:|---:|---:|---:|---|
| Forward proceeds | $12,397,350.00 | $12,397,350.00 | $12,397,350.00 | $0.00 | PASS |
| EUR borrowed | €10,186,344.07 | €10,186,344.07 | €10,186,344.07 | €0.00 | PASS |
| USD converted | $11,196,829.41 | $11,196,829.41 | $11,196,829.41 | $0.00 | PASS |
| Money-market proceeds | $11,721,307.56 | $11,721,307.56 | $11,721,307.56 | $0.00 | PASS |
| Initial put premium | $257,250.00 | $257,250.00 | $257,250.00 | $0.00 | PASS |
| Financed put premium | $269,300.02 | $269,300.02 | $269,300.02 | $0.00 | PASS |
| Put net proceeds | $11,272,299.98 | $11,272,299.98 | $11,272,299.98 | $0.00 | PASS |

### 3.4 Interpretation

The forward hedge calculation confirms that the company can lock in $12,397,350.00 in USD proceeds if the assigned forward quote is executable.

The money-market hedge demonstrates how borrowing EUR today, converting the borrowed funds into USD, and investing the USD proceeds creates a fixed settlement-date cash flow of $11,721,307.56.

The put option calculation confirms that the company can establish minimum net proceeds of $11,272,299.98 while retaining the opportunity to benefit from EUR appreciation. However, the financed premium reduces the net proceeds.

All seven hand-calculated values reconcile with the reported Excel workbook and independent LLM results to the nearest cent. This provides additional evidence that the model correctly applies the specified hedge formulas.

The hand verification establishes mathematical consistency under the stated assumptions but does not establish that the market quotes or financing rates are executable.

**Hand-verification status: PASS.**

## 4. Specification Retrospective

### 4.1 What Worked Well

The independent LLM was able to reproduce the forward, money-market, put option, call option, and unhedged calculations using only the Stage 2 specification and Stage 4 market-data memo. All 18 compared outcomes matched the Excel workbook to the nearest cent. The hand-verification calculations also reconciled with the reported results.

This demonstrates that the specification provided sufficient formulas, named ranges, and calculation instructions to reproduce the core model without access to the Excel workbook.

However, numerical agreement does not mean that the documentation was perfect. The LLM still had to make several assumptions and resolve conflicting information.

### 4.2 Documentation Weaknesses

First, the market-data memo contained conflicting USD interest rates of 4.60% and 4.62%. The LLM selected 4.62% because it appeared in the updated inputs table and completed CIP analysis. Although this was consistent with my workbook, another LLM could have selected the earlier rate and produced different results.

Second, the put and call strikes were still described as pending in the market-data memo. The LLM assumed that both strikes equaled the updated spot rate of 1.0992 based on the Stage 2 specification. This assumption was correct for my workbook, but the final strike values should have been explicitly documented.

Third, the LLM identified duplicate versions of Section 4 and an outdated statement in Section 5 indicating that the workbook had not yet been populated. These inconsistencies resulted from updating the document in stages without completing a final consistency review.

Finally, the firm's risk tolerance was not explicitly defined. The LLM assumed that maximizing guaranteed USD proceeds was the primary objective. Although reasonable, this assumption could influence the recommendation if management instead prioritized flexibility or participation in EUR appreciation.

### 4.3 Improvements for Specification Version 2

In a future version of the specification, I would:

- Establish one authoritative input table and explicitly state that finalized market inputs override earlier placeholders.
- Require numerical confirmation of all option strikes and premiums before independent execution.
- Clearly distinguish scenario-given assumptions, market observations, proxy rates, and executable bank quotes.
- Specify the firm's assumed risk posture and decision criteria.
- Include a final documentation consistency check to eliminate duplicate sections and outdated completion statements.
- Separate reference calculation results from the input documents where possible to strengthen independent validation.

### 4.4 Lessons Learned

The independent execution demonstrated that a model can produce consistent numerical results while still relying on assumptions that are not fully documented. A strong specification must communicate not only the formulas but also which inputs are authoritative, how conflicting information should be resolved, and what business objectives guide the recommendation.

I also learned that agreement between an LLM and a spreadsheet is not sufficient evidence of mathematical accuracy. Independent hand verification is necessary, particularly when the LLM has access to previously reported check figures.

The most important improvement is therefore not making the specification longer, but making it clearer, more consistent, and less dependent on undocumented assumptions.

## 5. Final Validation Conclusion

| Validation Component | Status |
|---|---|
| Independent LLM execution | PASS |
| Raw LLM output preserved | PASS |
| Comparison of 18 hedge outcomes | PASS |
| Independent hand verification | PASS |
| Covered interest parity | REVIEW |
| Documentation clarity | Improvements identified |
| Market quote executability | Requires confirmation |

The model is mathematically consistent under the specified assumptions. However, the covered interest parity discrepancy and the use of indicative market inputs require confirmation before executing an actual hedge.

The validated model provides the foundation for the CFO decision memo.
