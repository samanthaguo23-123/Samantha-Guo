# Stage 4 — Market Data Memo

**Project:** FIN 321 FX Hedging  
**Scenario:** 15 — Landing Gear  
**Market Data Date:** November 19, 2026  
**Currency Exposure:** EUR 10,500,000 receivable  
**Settlement Period:** 365 days

## 1. Market Data Sources

| Input | Value | Source | Observation / Publication Time | Notes |
|---|---|---|---|---|
| S0_in — EUR/USD spot | 1.0992 | European Central Bank (ECB) | November 19, 2026; approximately 14:10 CET fixing, published around 16:00 CET | Official daily reference rate used as a spot proxy; not a New York market-close quote |
| R_USD — 1-year USD rate | 4.62% (0.0462) | U.S. Department of the Treasury, Daily Treasury Par Yield Curve Rates | Observation: November 19, 2026; retrieved approximately 12:41 PM HST | 1-year Treasury yield used as a USD interest-rate proxy; not an executable deposit rate |
| R_FC — 1-year EUR rate | 3.037% (0.03037) | Investing.com, Germany 1-Year Bond Yield historical data | Observation: November 19, 2026; exact close time not supplied | German 1-year government bond yield used as a EUR interest-rate proxy; not an executable bank deposit rate |
| F0_in — 1-year forward | 1.1807 | Scenario 15 bank quote | Scenario assignment; original quote timestamp not supplied | Retained as the bank quote, not replaced by CIP |
| K_PUT — Put strike | Pending | Scenario convention | November 19, 2026 | To be set near the live spot |
| K_CALL — Call strike | Pending | Scenario convention | November 19, 2026 | To be set near the live spot |
| PREM_PUT — Put premium | 0.0245 USD/EUR | Scenario 15 | Scenario assignment | Original premium retained as an assumption |
| PREM_CALL — Call premium | 0.0448 USD/EUR | Stage 2 specification | Scenario specification | Original premium retained as an assumption |
| FC_AMT — Receivable | EUR 10,500,000 | Scenario 15 | Scenario assignment | Fixed contractual exposure |
| T_DAYS — Settlement period | 365 | Scenario 15 | Scenario assignment | Fixed contractual term |

**Spot source:** https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html

## 2. Spot Rate Selection

The ECB's EUR/USD reference rate for November 19, 2026 was 1.0992 USD per EUR. I selected this source because it provides an official, date-specific exchange rate that can be independently verified.

The ECB reference fixing is normally determined around 14:10 CET and published around 16:00 CET. It is not a tradable bank quote or a New York end-of-day close. I am documenting this distinction rather than treating the reference fixing as an executable market price.

## 3. Interest Rate Selection

Pending retrieval of November 19, 2026 one-year USD and EUR rates. The selected instruments, source timestamps, and reasons for using them will be documented here.
**USD rate selection:** I selected the Federal Reserve's 1-year constant-maturity U.S. Treasury yield (FRED series DGS1) as a transparent, publicly available proxy for a 1-year USD interest rate. The latest observation verified during retrieval was 4.60% on November 17, 2026. The November 19 market-close observation is pending verification. Because a Treasury yield is not the same as a bank deposit or borrowing rate, this proxy introduces a limitation into the covered interest parity comparison.

Source: https://fred.stlouisfed.org/series/DGS1

**EUR rate selection:** I selected the German 1-year government bond yield as a proxy for the EUR interest rate because Germany issues euro-denominated sovereign debt and its yields are publicly observable. Investing.com's historical data reports a yield of 3.037% for November 19, 2026. This is a sovereign bond yield rather than a bank borrowing or deposit rate, so it is an approximation for the covered interest parity calculation.

Source: https://www.investing.com/rates-bonds/germany-1-year-bond-yield-historical-data

## 4. Covered Interest Parity Comparison

The CIP-implied forward will be calculated using:

F_CIP = S0 × (1 + R_USD × 365/360) / (1 + R_FC × 365/360)

The bank's assigned forward quote is 1.1807 USD/EUR and will remain unchanged unless a requote is obtained.

The difference between the CIP-implied forward and the bank quote will be reported both in USD/EUR and in total USD on the EUR 10,500,000 receivable.

**Calculation status:** Pending interest-rate inputs.
## 4. Covered Interest Parity Comparison

Using the November 19, 2026 market-data inputs:

- EUR/USD spot rate: 1.0992
- USD 1-year interest rate: 4.62%
- EUR 1-year interest rate: 3.037%
- Settlement period: 365 days
- Day-count basis: 360
- Assigned bank forward quote: 1.1807 USD/EUR

**CIP-implied forward calculation:**

F_CIP = 1.0992 × [1 + 0.0462 × (365/360)] / [1 + 0.03037 × (365/360)]

**CIP-implied forward = 1.116315 USD/EUR**

**Comparison with the bank quote:**

- Bank forward quote: 1.180700 USD/EUR
- CIP-implied forward: 1.116315 USD/EUR
- Difference (CIP minus bank): −0.064385 USD/EUR
- CIP-implied proceeds on €10,500,000: $11,721,307.56
- Bank-quoted forward proceeds: $12,397,350.00
- Difference in proceeds: −$676,042.44

**Interpretation:** The bank's assigned forward quote is substantially higher than the forward rate implied by covered interest parity using the selected government-yield proxies. The difference is approximately 5.45% of the bank quote.

The bank quote has been retained rather than replaced by the CIP-implied rate. Because government yields are proxies rather than executable borrowing and lending rates, the discrepancy does not by itself establish an arbitrage opportunity. The difference warrants further investigation and potentially a bank requote.

**Expected parity status:** REVIEW.
## 5. Workbook Population and Validation

The workbook will be populated through its existing named-range input cells.

After population, I will recheck the forward hedge, money-market hedge, option calculations, parity status, 11-row sensitivity table, and sensitivity chart.

**Status:** Not yet populated or validated with Stage 4 market inputs.

## 6. FX Hedging Lab Cross-Check

**Date:** November 19, 2026  

I compared my updated Excel workbook with the course FX Hedging Lab using the November 19 market inputs.

### Results

| Calculation | Result |
|---|---:|
| Forward hedge proceeds | $12,397,350.00 |
| EUR borrowed today | €10,186,344.07 |
| EUR converted to USD | $11,196,829.41 |
| Money-market hedge proceeds | $11,721,307.56 |

### Discrepancy and Resolution

The FX Lab initially showed money-market proceeds of $11,542,158, which differed from my Excel workbook.

After reviewing the inputs, I identified that the FX Lab expected interest rates entered as percentages rather than decimal fractions.

I corrected the interest-rate inputs to 4.62% for USD and 3.037% for EUR. The FX Lab then produced money-market proceeds of $11,721,307.56, matching my workbook.

The discrepancy was caused by the FX Lab input format rather than a workbook formula error.

### Put Option Cross-Check

The FX Hedging Lab reported protected minimum proceeds of $11,272,299.98.

I independently checked the Option_Hedge worksheet in my Excel workbook. The workbook calculates an initial put premium of $257,250.00, a financed premium cost of $269,300.02, and protected minimum proceeds of $11,272,299.98.

The FX Lab and Excel workbook agree to the nearest cent.

**Final cross-check status:** PASS — Forward hedge, money-market hedge, and put option calculations match the FX Hedging Lab.
