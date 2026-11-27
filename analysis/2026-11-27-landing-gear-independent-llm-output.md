# **Independent FX Hedging Analysis — Scenario 15: Landing Gear**

**Market data date:** November 19, 2026\
**Foreign currency exposure:** EUR 10,500,000 receivable\
**Settlement period:** 365 days\
**Reporting currency:** USD\
**Prepared for:** Chief Financial Officer (CFO)

This analysis uses exclusively the two provided documents:

- Stage 2 — FX Hedging Model Specification
- Stage 4 — Market Data Memo dated November 19, 2026

The hedge outcomes are independently recalculated using the formulas in the Stage 2 specification and the updated market inputs in the Stage 4 memo. The reported check figures are used for reconciliation after calculation. No additional external market data is used.

## **1. Executive summary**

The company faces foreign exchange risk because its EUR 10,500,000 receivable must eventually be converted into U.S. dollars. Depreciation of the euro would reduce the company's USD proceeds.

Highest guaranteed proceeds under the provided inputs

# **$12,397,350.00**

Forward hedge

Advantage over money-market hedge

## **$676,042.44**

Advantage over baseline unhedged position

## **$855,750.00**

| Strategy           | Baseline USD proceeds | Guaranteed minimum |
| ------------------ | --------------------- | ------------------ |
| Forward hedge      | $12,397,350.00        | $12,397,350.00     |
| Money-market hedge | $11,721,307.56        | $11,721,307.56     |
| Unhedged           | $11,541,600.00        | None               |
| Put option hedge   | $11,272,299.98        | $11,272,299.98     |

The baseline assumes the settlement exchange rate equals the initial spot rate of 1.0992 USD/EUR.

The forward hedge produces the highest USD proceeds in all 11 prescribed sensitivity scenarios. However, the assigned forward rate differs substantially from the rate implied by covered interest parity.

**Recommendation:** Pursue the forward hedge, conditional upon obtaining confirmation that the assigned bank quote remains executable for the entire receivable. If the quote cannot be obtained, reassess the available hedging alternatives using consistent, executable market rates.

A purchased EUR call option is calculated separately because it protects a foreign currency payable rather than a receivable.

## **2. Model inputs and assumptions**

The Stage 4 market-data inputs replace the initial market-dependent placeholders in the Stage 2 specification.

| Input                    | Named range | Value            |
| ------------------------ | ----------- | ---------------- |
| EUR receivable           | `FC_AMT`    | €10,500,000      |
| Initial spot rate        | `S0_in`     | 1.0992 USD/EUR   |
| Assigned forward rate    | `F0_in`     | 1.1807 USD/EUR   |
| Annual USD interest rate | `R_USD`     | 4.62%            |
| Annual EUR interest rate | `R_FC`      | 3.037%           |
| Put strike               | `K_PUT`     | 1.0992 USD/EUR\* |
| Call strike              | `K_CALL`    | 1.0992 USD/EUR\* |
| Put premium              | `PREM_PUT`  | 0.0245 USD/EUR   |
| Call premium             | `PREM_CALL` | 0.0448 USD/EUR   |
| Settlement period        | `T_DAYS`    | 365 days         |
| Day-count basis          | `BASIS`     | 360 days         |
| Sensitivity increment    | `STEP_FRAC` | 1%               |

The spot rate and interest rates are taken from the Stage 4 market-data table, while the assigned forward quote and option premiums remain unchanged.&#x20;

2026-11-19-landing-gear-market-data-memo.md



\*Both option strikes are assumed to equal the updated spot rate of 1.0992 USD/EUR. The Stage 4 memo lists the strikes as pending, but the Stage 2 specification states that both strikes are initially assumed to equal spot.&#x20;

spec.md



Additional assumptions:

- The entire EUR receivable is collected on time.
- All hedging strategies cover 100% of the exposure.
- Simple interest is calculated using ACT/360.
- Option premiums are paid upfront and carried forward to settlement.
- Transaction costs, taxes, bid-ask spreads, hedge accounting effects, and counterparty risks are excluded.
- Interest rates, premiums, strikes, and forward quotes remain constant throughout the sensitivity analysis.

These assumptions follow the Stage 2 model constraints.&#x20;

spec.md



## **3. Preliminary calculations**

Before evaluating each hedging strategy, calculate the interest accumulation factors.

### **3.1 Time adjustment**

\\[ t=\frac{365}{360}=1.013888889 \\]

### **3.2 USD accumulation factor**

\\[ DF\_{USD}=1+R\_{USD}\times t \\]

\\[ =1+0.0462\times\frac{365}{360} \\]

\\[ \boxed{DF\_{USD}=1.0468416667} \\]

The effective USD interest over the settlement period is 4.684167%.

### **3.3 EUR accumulation factor**

\\[ DF\_{EUR}=1+R\_{EUR}\times t \\]

\\[ =1+0.03037\times\frac{365}{360} \\]

\\[ \boxed{DF\_{EUR}=1.0307918056} \\]

The effective EUR interest over the settlement period is 3.079181%.

Both accumulation factors follow the formulas specified in Stage 2.&#x20;

spec.md



All subsequent calculations retain full numerical precision, with rounding applied only to displayed results.

## **4. Independent hedge calculations**

### **4.1 Unhedged position**

Under the unhedged strategy, the company receives EUR 10,500,000 at settlement and converts the entire amount into USD at the prevailing exchange rate.

**Formula:**

\\[ USD\_{Unhedged}=FC\_{AMT}\times S_T \\]

Using the baseline assumption:

\\[ S_T=1.0992 \\]

\\[ USD\_{Unhedged}=10,500,000\times1.0992 \\]

\\[ \boxed{USD\_{Unhedged}=\\$11,541,600.00} \\]

The company does not incur an option premium or enter into a financing arrangement. However, the final USD proceeds remain completely exposed to movements in EUR/USD.

For every 0.01 USD/EUR change in the settlement exchange rate, the company's proceeds change by $105,000.

### **4.2 Forward hedge**

The company enters into a forward contract to sell EUR 10,500,000 in 365 days at the assigned exchange rate of 1.1807 USD/EUR.

**Formula:**

\\[ USD\_{Forward}=FC\_{AMT}\times F_0 \\]

\\[ =10,500,000\times1.1807 \\]

\\[ \boxed{USD\_{Forward}=\\$12,397,350.00} \\]

**Benefit relative to the baseline unhedged position:**

\\[ 12,397,350-11,541,600 \\]

\\[ =\boxed{\\$855,750.00} \\]

The forward hedge eliminates exchange-rate uncertainty and guarantees the contracted USD proceeds, assuming the forward contract is available and both parties fulfill their obligations.

Its principal disadvantage is that the company cannot benefit from euro appreciation beyond the contracted forward rate.

### **4.3 Money-market hedge**

The money-market hedge creates a synthetic forward transaction by borrowing euros today, converting them into USD, and investing the USD until settlement.

The three-step calculation follows Section 5.4 of the specification.&#x20;

spec.md



Today — establish the hedge

Borrow EUR

**€10,186,344.07**

Convert at 1.0992

**$11,196,829.41**

365 days of interest

Settlement — close the hedge

Repay EUR loan using receivable

**€10,500,000.00**

Receive USD investment

### **$11,721,307.56**

**Step 1 — Borrow the present value of the EUR receivable**

\\[ BORROW\_{EUR}=\frac{FC\_{AMT}}{DF\_{EUR}} \\]

\\[ =\frac{10,500,000}{1.0307918056} \\]

\\[ \boxed{BORROW\_{EUR}=\text{€}10,186,344.07} \\]

EUR interest expense:

\\[ 10,500,000-10,186,344.07 \\]

\\[ =\text{€}313,655.93 \\]

At settlement, the EUR loan balance equals the contractual receivable.

**Step 2 — Convert borrowed euros into USD**

\\[ USD\_{Now}=BORROW\_{EUR}\times S_0 \\]

\\[ =10,186,344.073952857\times1.0992 \\]

\\[ \boxed{USD\_{Now}=\\$11,196,829.41} \\]

**Step 3 — Invest the USD proceeds**

\\[ USD\_{MM}=USD\_{Now}\times DF\_{USD} \\]

\\[ =11,196,829.40608898\times1.0468416667 \\]

\\[ \boxed{USD\_{MM}=\\$11,721,307.56} \\]

USD interest income is approximately $524,478.15.

**Benefit relative to the baseline unhedged position:**

\\[ 11,721,307.56-11,541,600 \\]

\\[ =\boxed{\\$179,707.56} \\]

The money-market hedge eliminates exchange-rate uncertainty under the specified borrowing and investment assumptions. However, it produces $676,042.44 less than the assigned forward hedge and requires access to EUR borrowing and USD investment facilities.

### **4.4 EUR put option hedge**

The company purchases a EUR put option, giving it the right, but not the obligation, to sell its euros at the strike price.

The strike is assumed to equal the updated spot rate of 1.0992 USD/EUR.

**Step 1 — Calculate the upfront premium**

\\[ PUT\_{Premium}=FC\_{AMT}\times PREM\_{PUT} \\]

\\[ =10,500,000\times0.0245 \\]

\\[ \boxed{PUT\_{Premium}=\\$257,250.00} \\]

**Step 2 — Calculate the settlement-date premium cost**

\\[ Premium\_{FV}=PUT\_{Premium}\times DF\_{USD} \\]

\\[ =257,250\times1.0468416667 \\]

\\[ \boxed{Premium\_{FV}=\\$269,300.02} \\]

The premium financing or opportunity cost is $12,050.02.

Under the specification's sign convention:

\\[ FV\_{PREM\\\_PUT}=-269,300.02 \\]

**Step 3 — Calculate net settlement proceeds**

\\[ USD\_{Put}(S_T) \\]

\\[ =FC\_{AMT}\times\max(S_T,K\_{PUT}) \\]

\\[ +FV\_{PREM\\\_PUT} \\]

Substituting the inputs:

\\[ =10,500,000\times\max(S_T,1.0992) \\]

\\[ -269,300.01875 \\]

**Step 4 — Calculate the protected minimum proceeds**

\\[ USD\_{Floor}=10,500,000\times1.0992 \\]

\\[ -269,300.01875 \\]

\\[ \boxed{USD\_{Floor}=\\$11,272,299.98} \\]

At settlement rates below 1.0992, the company exercises the put and receives the protected minimum. Above 1.0992, the company allows the option to expire and converts the receivable at the more favorable market rate.

### **Put option payoff structure**

Net put proceeds

Unhedged proceeds

The put option provides downside protection while preserving the opportunity to benefit from euro appreciation. Nevertheless, its premium reduces the net proceeds under every scenario relative to an otherwise identical costless option.

### **4.5 EUR call option**

The Stage 2 specification identifies the EUR call option as a reference calculation rather than a suitable standalone hedge for the company's EUR receivable. A purchased EUR call protects against euro appreciation, which is primarily a risk for a EUR payable.&#x20;

spec.md



Nevertheless, both call option outcomes specified in the document are calculated below.

**Step 1 — Calculate the upfront call premium**

\\[ CALL\_{Premium}=10,500,000\times0.0448 \\]

\\[ \boxed{CALL\_{Premium}=\\$470,400.00} \\]

**Step 2 — Calculate the settlement-date premium cost**

\\[ Premium\_{FV}=470,400\times1.0468416667 \\]

\\[ \boxed{Premium\_{FV}=\\$492,434.32} \\]

Under the specification's sign convention:

\\[ FV\_{PREM\\\_CALL}=-492,434.32 \\]

**Step 3 — Calculate standalone purchased call payoff**

\\[ CALL\_{Payoff}(S_T) \\]

\\[ =10,500,000\times\max(S_T-1.0992,0) \\]

\\[ -492,434.32 \\]

At the baseline settlement rate of 1.0992:

\\[ =10,500,000\times0-492,434.32 \\]

\\[ \boxed{CALL\_{Payoff}=-\\$492,434.32} \\]

The option has no intrinsic value at the baseline rate, resulting in a loss equal to the financed premium.

**Step 4 — Calculate the hypothetical EUR payable hedge**

The specification provides the following formula for a EUR payable:

\\[ USD\_{Call}=FC\_{AMT}\times\min(S_T,K\_{CALL}) \\]

\\[ -FV\_{PREM\\\_CALL} \\]

At the baseline settlement rate:

\\[ =10,500,000\times1.0992+492,434.32 \\]

\\[ \boxed{USD\_{Call}=\\$12,034,034.32} \\]

This represents the maximum USD outlay for a hypothetical EUR 10,500,000 payable hedged with the call option.

It is an expenditure rather than revenue and therefore must not be directly ranked against the receivable hedge proceeds.

## **5. Covered interest parity evaluation**

Covered interest parity (CIP) establishes the theoretical relationship between spot exchange rates, forward exchange rates, and domestic and foreign interest rates.

### **5.1 Calculate the CIP-implied forward rate**

Following the specification:

\\[ F\_{CIP}=S_0\times\frac{DF\_{USD}}{DF\_{EUR}} \\]

\\[ =1.0992\times \frac{1+0.0462(365/360)} {1+0.03037(365/360)} \\]

\\[ =1.0992\times \frac{1.0468416667}{1.0307918056} \\]

\\[ \boxed{F\_{CIP}=1.1163150054} \\]

### **5.2 Compare the implied and assigned forward rates**

\\[ PARITY\_{DIFF}=F\_{CIP}-F_0 \\]

\\[ =1.1163150054-1.1807 \\]

\\[ \boxed{PARITY\_{DIFF}=-0.0643849946} \\]

The assigned forward rate is approximately 0.064385 USD/EUR higher than the theoretical rate.

### **5.3 Percentage difference**

\\[ PARITY\_{PCT}= \left|\frac{F\_{CIP}-F_0}{F_0}\right| \\]

\\[ =\left|\frac{-0.0643849946}{1.1807}\right| \\]

\\[ \boxed{PARITY\_{PCT}=5.4531\\%} \\]

### **Covered interest parity comparison**

Assigned forward rate

**1.180700**

CIP-implied forward rate

**1.116315**

Actual deviation

# **5.4531%**

Permitted tolerance

# **0.05%**

**Parity status**

REVIEW

The specification requires a REVIEW status whenever the percentage difference exceeds 0.05%.&#x20;

spec.md



### **5.4 Dollar impact of the parity discrepancy**

| Calculation                     | Result         |
| ------------------------------- | -------------- |
| Assigned forward rate           | 1.180700       |
| CIP-implied forward rate        | 1.116315       |
| Difference (CIP minus assigned) | −0.064385      |
| Assigned forward proceeds       | $12,397,350.00 |
| CIP-implied proceeds            | $11,721,307.56 |
| Difference in USD proceeds      | −$676,042.44   |

The CIP-implied proceeds equal the money-market hedge proceeds, which confirms the mathematical consistency of the money-market hedge.

### **5.5 Interpretation**

The discrepancy is economically significant. Under the model's assumptions, the assigned forward hedge produces substantially more USD than the equivalent money-market hedge.

However, the discrepancy does not establish an executable arbitrage opportunity because the documents acknowledge that:

- The ECB reference rate is not an executable spot quote.
- The USD Treasury yield is a proxy rather than a bank investment rate.
- The German government bond yield is a proxy rather than an executable EUR borrowing rate.
- The assigned forward quote has no original timestamp.
- Bid-ask spreads and transaction costs are excluded.

The spot, interest rates, and forward rate may therefore represent different market conditions and pricing conventions. The bank quote should be confirmed before any transaction is executed.

## **6. Sensitivity analysis**

The specification requires 11 settlement exchange-rate scenarios, ranging from a 5% depreciation to a 5% appreciation of the euro, in increments of 1%.&#x20;

spec.md



The settlement rate is calculated as:

\\[ S_T=S_0(1+n\times0.01) \\]

Where:

\\[ n=-5,-4,\ldots,0,\ldots,4,5 \\]

For example, under a 5% euro depreciation:

\\[ S_T=1.0992(1-0.05)=1.04424 \\]

### **6.1 Receivable hedge sensitivity table**

All proceeds are expressed in settlement-date USD. Exchange rates are displayed to six decimal places to preserve the sensitivity increments.

| Change | Settlement rate | Unhedged          | Forward           | Money-market      | Put option        |
| ------ | --------------- | ----------------- | ----------------- | ----------------- | ----------------- |
| −5%    | 1.044240        | 10,964,520.00     | 12,397,350.00     | 11,721,307.56     | 11,272,299.98     |
| −4%    | 1.055232        | 11,079,936.00     | 12,397,350.00     | 11,721,307.56     | 11,272,299.98     |
| −3%    | 1.066224        | 11,195,352.00     | 12,397,350.00     | 11,721,307.56     | 11,272,299.98     |
| −2%    | 1.077216        | 11,310,768.00     | 12,397,350.00     | 11,721,307.56     | 11,272,299.98     |
| −1%    | 1.088208        | 11,426,184.00     | 12,397,350.00     | 11,721,307.56     | 11,272,299.98     |
| **0%** | **1.099200**    | **11,541,600.00** | **12,397,350.00** | **11,721,307.56** | **11,272,299.98** |
| +1%    | 1.110192        | 11,657,016.00     | 12,397,350.00     | 11,721,307.56     | 11,387,715.98     |
| +2%    | 1.121184        | 11,772,432.00     | 12,397,350.00     | 11,721,307.56     | 11,503,131.98     |
| +3%    | 1.132176        | 11,887,848.00     | 12,397,350.00     | 11,721,307.56     | 11,618,547.98     |
| +4%    | 1.143168        | 12,003,264.00     | 12,397,350.00     | 11,721,307.56     | 11,733,963.98     |
| +5%    | 1.154160        | 12,118,680.00     | 12,397,350.00     | 11,721,307.56     | 11,849,379.98     |

**Highest-proceeds strategy:** Forward hedge in all 11 scenarios.

**Best active hedge:** Forward hedge in all 11 scenarios.

There are no ties within the prescribed sensitivity range.

### **6.2 Sensitivity chart**

### **FX Hedging Sensitivity Analysis — Scenario 15**

Net USD proceeds at settlement

Forward hedge

Money-market hedge

Unhedged

Put option

The forward and money-market lines remain constant because their USD proceeds are fixed.

The unhedged position increases proportionally with euro appreciation. The put option remains constant below its strike and increases above its strike after deducting the financed premium.

### **6.3 Hedge profit or loss relative to no hedge**

Hedge profit is defined by the specification as the difference between the hedged proceeds and the unhedged proceeds at the same settlement exchange rate.

| EUR/USD change | Forward benefit | Money-market benefit | Put benefit  |
| -------------- | --------------- | -------------------- | ------------ |
| −5%            | $1,432,830.00   | $756,787.56          | $307,779.98  |
| −4%            | $1,317,414.00   | $641,371.56          | $192,363.98  |
| −3%            | $1,201,998.00   | $525,955.56          | $76,947.98   |
| −2%            | $1,086,582.00   | $410,539.56          | −$38,468.02  |
| −1%            | $971,166.00     | $295,123.56          | −$153,884.02 |
| 0%             | $855,750.00     | $179,707.56          | −$269,300.02 |
| +1%            | $740,334.00     | $64,291.56           | −$269,300.02 |
| +2%            | $624,918.00     | −$51,124.44          | −$269,300.02 |
| +3%            | $509,502.00     | −$166,540.44         | −$269,300.02 |
| +4%            | $394,086.00     | −$281,956.44         | −$269,300.02 |
| +5%            | $278,670.00     | −$397,372.44         | −$269,300.02 |

A negative hedge benefit represents an opportunity cost relative to remaining unhedged. It does not necessarily represent an accounting loss.

The forward hedge generates a positive benefit across every prescribed scenario. The money-market hedge outperforms the unhedged position through the +1% scenario, while the put option outperforms the unhedged position when the euro depreciates sufficiently to recover the premium cost.

### **6.4 Call option sensitivity analysis**

The call option is presented separately to avoid confusing receivable proceeds with hypothetical payable costs.

| Change | Settlement rate | Standalone call net payoff | Hypothetical payable USD outlay |
| ------ | --------------- | -------------------------- | ------------------------------- |
| −5%    | 1.044240        | −$492,434.32               | $11,456,954.32                  |
| −4%    | 1.055232        | −$492,434.32               | $11,572,370.32                  |
| −3%    | 1.066224        | −$492,434.32               | $11,687,786.32                  |
| −2%    | 1.077216        | −$492,434.32               | $11,803,202.32                  |
| −1%    | 1.088208        | −$492,434.32               | $11,918,618.32                  |
| 0%     | 1.099200        | −$492,434.32               | $12,034,034.32                  |
| +1%    | 1.110192        | −$377,018.32               | $12,034,034.32                  |
| +2%    | 1.121184        | −$261,602.32               | $12,034,034.32                  |
| +3%    | 1.132176        | −$146,186.32               | $12,034,034.32                  |
| +4%    | 1.143168        | −$30,770.32                | $12,034,034.32                  |
| +5%    | 1.154160        | $84,645.68                 | $12,034,034.32                  |

The call produces a positive standalone net payoff only in the +5% scenario within the prescribed sensitivity range.

If purchased alongside the existing EUR receivable, the call would increase exposure to euro appreciation rather than protect against depreciation. Consequently, it is not recommended as a hedge for this exposure.

### **6.5 Interactive settlement-rate comparison**

The following calculation allows the settlement rate to vary beyond the prescribed ±5% range while keeping the other document inputs constant.

Settlement exchange rate

# **1.0992**

Euro depreciation

Euro appreciation

Change from initial spot: 0.00%

Forward

$12,397,350.00

Money-market

$11,721,307.56

Unhedged

$11,541,600.00

Put option

$11,272,299.98

Standalone call net payoff

-$492,434.32

Highest-proceeds strategy

**Forward**

Reset to baseline

## **7. Break-even analysis**

Although the forward hedge dominates within the prescribed sensitivity range, it is important to identify the exchange rates at which alternative strategies become more attractive.

### **7.1 Unhedged versus forward hedge**

\\[ FC\_{AMT}\times S_T=FC\_{AMT}\times F_0 \\]

\\[ \boxed{S_T=1.1807} \\]

The unhedged position outperforms the forward hedge when EUR/USD exceeds 1.1807, representing euro appreciation of approximately 7.41% relative to the initial spot rate.

### **7.2 Unhedged versus money-market hedge**

\\[ S_T=\frac{USD\_{MM}}{FC\_{AMT}} \\]

\\[ =\frac{11,721,307.55685253}{10,500,000} \\]

\\[ \boxed{S_T=1.1163150054} \\]

The unhedged position outperforms the money-market hedge above this settlement rate.

### **7.3 Put option versus unhedged position**

The put option's premium-adjusted break-even rate is:

\\[ S_T=K\_{PUT}-\frac{Premium\_{FV}}{FC\_{AMT}} \\]

\\[ =1.0992-\frac{269,300.01875}{10,500,000} \\]

\\[ \boxed{S_T=1.0735523792} \\]

The put option outperforms the unhedged position when EUR/USD falls below approximately 1.073552.

### **7.4 Put option versus forward hedge**

Above the put strike:

\\[ FC\_{AMT}\times S_T-Premium\_{FV} \\]

\\[ =FC\_{AMT}\times F_0 \\]

Solving for the settlement rate:

\\[ S_T=F_0+\frac{Premium\_{FV}}{FC\_{AMT}} \\]

\\[ =1.1807+\frac{269,300.01875}{10,500,000} \\]

\\[ \boxed{S_T=1.2063476208} \\]

The put option outperforms the forward hedge only when EUR/USD exceeds approximately 1.206348, representing euro appreciation of 9.75%.

### **7.5 Put option versus money-market hedge**

\\[ S_T=\frac{USD\_{MM}+Premium\_{FV}}{FC\_{AMT}} \\]

\\[ =\frac{11,721,307.55685253+269,300.01875} {10,500,000} \\]

\\[ \boxed{S_T=1.1419626262} \\]

The put option outperforms the money-market hedge above this rate.

### **7.6 Standalone call option break-even**

\\[ S_T=K\_{CALL}+\frac{Premium\_{FV}}{FC\_{AMT}} \\]

\\[ =1.0992+\frac{492,434.32}{10,500,000} \\]

\\[ \boxed{S_T=1.1460985067} \\]

The standalone call option produces a positive net payoff above this exchange rate.

### **Break-even summary**

| Comparison                | Break-even rate | Change from initial spot |
| ------------------------- | --------------- | ------------------------ |
| Put vs. unhedged          | 1.073552        | −2.33%                   |
| Unhedged vs. money-market | 1.116315        | +1.56%                   |
| Put vs. money-market      | 1.141963        | +3.89%                   |
| Standalone call profit    | 1.146099        | +4.27%                   |
| Unhedged vs. forward      | 1.180700        | +7.41%                   |
| Put vs. forward           | 1.206348        | +9.75%                   |

These results establish the conditions under which the forward hedge would no longer produce the highest proceeds. The sensitivity range is not a forecast, and the documents do not establish the probabilities of these exchange rates occurring.

## **8. Strategy comparison and risk assessment**

### **Baseline proceeds by strategy**

Forward hedge

$12,397,350.00

Money-market hedge

$11,721,307.56

Unhedged position

$11,541,600.00

Put option hedge

$11,272,299.98

Baseline settlement rate: 1.0992 USD/EUR. Bars start at zero.

| Evaluation criterion        | Forward | Money-market | Put option          | Unhedged |
| --------------------------- | ------- | ------------ | ------------------- | -------- |
| Eliminates downside FX risk | Yes     | Yes          | Establishes a floor | No       |
| Retains appreciation upside | No      | No           | Yes                 | Yes      |
| Upfront option premium      | None    | None         | $257,250            | None     |
| Requires EUR borrowing      | No      | Yes          | No                  | No       |
| Predictable USD proceeds    | Fixed   | Fixed        | Minimum guaranteed  | Variable |
| Baseline ranking            | 1st     | 2nd          | 4th                 | 3rd      |

The forward hedge offers the strongest combination of guaranteed proceeds and operational simplicity under the assigned assumptions.

The money-market hedge provides comparable exchange-rate certainty but introduces borrowing requirements and produces lower modeled proceeds.

The put option is appropriate if management values upside participation sufficiently to accept a lower guaranteed minimum and the cost of the option premium.

Remaining unhedged would expose the company to unnecessary exchange-rate uncertainty if its primary objective is protecting the USD value of the receivable.

## **9. Independent reconciliation and validation**

After independently calculating the results, the forward hedge, money-market hedge, CIP-implied rate, and put option calculations were compared with the reported values in the Stage 4 memo.

| Calculation            | Independent result | Memo result    | Difference |
| ---------------------- | ------------------ | -------------- | ---------- |
| Forward proceeds       | $12,397,350.00     | $12,397,350.00 | $0.00      |
| EUR borrowing          | €10,186,344.07     | €10,186,344.07 | €0.00      |
| Initial USD conversion | $11,196,829.41     | $11,196,829.41 | $0.00      |
| Money-market proceeds  | $11,721,307.56     | $11,721,307.56 | $0.00      |
| CIP-implied forward\*  | 1.116315           | 1.116315       | 0.000000   |
| Initial put premium    | $257,250.00        | $257,250.00    | $0.00      |
| Financed put premium   | $269,300.02        | $269,300.02    | $0.00      |
| Put protected minimum  | $11,272,299.98     | $11,272,299.98 | $0.00      |

\*Compared at the six-decimal precision reported in the memo.

The reported Stage 4 check figures are contained in its CIP comparison and FX Hedging Lab cross-check sections.&#x20;

2026-11-19-landing-gear-market-data-memo.md

2026-11-19-landing-gear-market-data-memo.md



All overlapping numerical results agree to their reported precision.

### **Model validation checks**

Forward hedge calculation

$12,397,350.00

PASS

EUR loan repayment

€10,500,000.00; residual €0.00

PASS

Money-market proceeds equal CIP proceeds

$11,721,307.56

PASS

Put floor validation

Residual $0.00

PASS

Option premium treatment

Settlement-date cost deducted exactly once

PASS

Sensitivity scenario count

11 scenarios, −5% through +5%

PASS

Fixed hedge proceeds

Forward and money-market remain constant

PASS

Put payoff behavior

Flat below strike; increasing above strike

PASS

Covered interest parity

5.4531% exceeds 0.05% tolerance

REVIEW

The parity warning is not evidence of a calculation error. It is evidence that the supplied market inputs do not satisfy the model's parity tolerance.

The Stage 4 memo does not provide calculated call option outcomes for reconciliation. The call results in this analysis are therefore independently derived using the reference formulas from Stage 2.

Workbook-level checks, including named-range integrity, worksheet formatting, and automatic recalculation, cannot be verified because the workbook itself was not provided.

## **10. Missing information, ambiguities, and limitations**

The two documents provide sufficient information to calculate all requested hedge outcomes, but several limitations affect the reliability of the final business recommendation.

| Issue                                     | Assumption or resolution                                   | Potential impact                                              |
| ----------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------- |
| Put strike is pending                     | Set to updated spot of 1.0992                              | Actual option protection could differ                         |
| Call strike is pending                    | Set to updated spot of 1.0992                              | Actual call payoff could differ                               |
| Forward quote timestamp missing           | Retain assigned rate of 1.1807                             | Quote may be outdated or unavailable                          |
| Option premiums are indicative            | Retain original assigned premiums                          | Premiums may not reflect updated strikes or market conditions |
| Conflicting USD interest-rate information | Use 4.62% from the updated table and completed CIP section | Earlier section references 4.60% and pending verification     |
| EUR borrowing rate unavailable            | Use German government bond yield of 3.037%                 | Actual borrowing costs may be higher                          |
| USD investment rate unavailable           | Use Treasury yield of 4.62%                                | Actual investment returns may differ                          |
| Non-executable spot reference             | Use ECB reference rate of 1.0992                           | Actual conversion proceeds may differ                         |
| Transaction costs unavailable             | Assume zero incremental costs                              | Net hedge benefits may be overstated                          |
| Risk tolerance not specified              | Prioritize guaranteed USD proceeds                         | CFO may instead prioritize flexibility                        |
| Exchange-rate probabilities unavailable   | Use deterministic sensitivity analysis                     | Expected returns cannot be reliably calculated                |

### **10.1 Inconsistencies within the Stage 4 memo**

The memo contains several apparent drafting or version-control inconsistencies.

First, its market-data table provides a USD interest rate of 4.62%, while Section 3 refers to an earlier verified observation of 4.60% and states that the November 19 observation is pending. The completed CIP comparison subsequently uses 4.62%.

I use 4.62% because it appears in the updated market-data table and the completed numerical analysis.&#x20;

2026-11-19-landing-gear-market-data-memo.md

2026-11-19-landing-gear-market-data-memo.md

2026-11-19-landing-gear-market-data-memo.md



Second, Section 4 appears twice. The first version indicates that calculations are pending, while the second contains completed results. The later, completed section is treated as the operative version.

Third, Section 5 states that the workbook has not yet been populated or validated. However, Section 6 reports successful workbook and FX Lab cross-checks. This appears to be an outdated status statement that was not removed after subsequent work was completed.

These inconsistencies do not prevent numerical execution of the model but reduce the clarity of the documentation.

### **10.2 Option pricing limitation**

The assumption that both strikes equal the updated spot rate is supported by the Stage 2 convention. However, the original premiums are retained even though the strike and spot inputs have changed.

In practice, option premiums depend on the strike, maturity, market volatility, interest rates, and other pricing factors.

The documents do not provide sufficient information to independently reprice the options. Consequently, both option analyses represent hypothetical outcomes using the assigned premiums, rather than verified executable option contracts.

### **10.3 Forward quote reliability**

The assigned forward rate is the most material uncertainty in the analysis.

The quoted rate of 1.1807 is substantially higher than the CIP-implied rate of 1.116315. Because the forward quote has no documented observation date, it may not represent the same market environment as the updated spot and interest rates.

If the forward were instead available only at the theoretical CIP rate, its proceeds would be:

\\[ 10,500,000\times1.1163150054 \\]

\\[ =\\$11,721,307.56 \\]

This would eliminate the modeled $676,042.44 advantage over the money-market hedge.

Therefore, the recommendation depends materially on confirming the forward quote.

## **11. CFO recommendation**

**Recommended strategy: Hedge 100% of the EUR 10,500,000 receivable using a forward contract, subject to confirmation of the assigned forward rate.**

Based on the provided market inputs, the forward hedge guarantees USD proceeds of $12,397,350, exceeding the money-market hedge by $676,042.44 and the baseline unhedged position by $855,750. It also produces the highest USD proceeds under all 11 settlement exchange-rate scenarios.

The put option provides flexibility and downside protection, but its financed premium of $269,300.02 reduces guaranteed minimum proceeds to $11,272,299.98. The euro would need to appreciate approximately 9.75% from its initial spot rate before the put option outperforms the assigned forward contract. Purchasing a EUR call option is not appropriate because it does not protect the receivable against euro depreciation.

Nevertheless, the assigned forward quote produces a covered interest parity deviation of 5.4531%, substantially exceeding the model's tolerance of 0.05%. This discrepancy raises concerns regarding the consistency and executability of the underlying market inputs.

Before implementation, management should obtain a binding 365-day forward quote for the full exposure, confirm executable EUR borrowing and USD investment rates, and obtain updated option premiums and strikes. If the bank confirms the forward rate of 1.1807, the company should proceed with the forward hedge. Otherwise, management should recalculate the alternatives using consistent market data and select the strategy that provides the most favorable risk-adjusted outcome.

## **12. Final conclusion**

The two documents are sufficiently detailed to independently execute the core hedging model. The recalculated forward, money-market, put option, and covered interest parity results reconcile with the Stage 4 memo to the reported numerical precision. The call option reference calculations and sensitivity analysis can also be completed using the provided formulas.

The primary weakness is not mathematical accuracy but market-input consistency, particularly the assigned forward quote, pending option strikes, indicative option premiums, and use of sovereign yields as proxies for executable financing rates.

| Final assessment                              | Result                                           |
| --------------------------------------------- | ------------------------------------------------ |
| Independent numerical execution               | PASS                                             |
| Reconciliation with Stage 4 check figures     | PASS                                             |
| Sensitivity analysis                          | PASS                                             |
| Covered interest parity                       | REVIEW                                           |
| Documentation sufficiency for model execution | Sufficient with disclosed assumptions            |
| Market data readiness for actual execution    | Requires confirmation                            |
| Recommended strategy                          | Forward hedge, conditional on quote verification |

**The forward hedge is the preferred strategy under the supplied inputs, but the company should verify the executability of the forward quote before committing to the transaction.**