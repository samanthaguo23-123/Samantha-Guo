# FX Hedging Decision Memo — Scenario 15: Landing Gear

**To:** Chief Financial Officer  
**From:** Samantha Guo, Financial Analyst  
**Date:** November 27, 2026  
**Subject:** Recommended Hedging Strategy for EUR 10.5 Million Receivable  
**Market Data Date:** November 19, 2026

## A. Exposure Summary

The company expects to receive EUR 10,500,000 in 365 days from its landing gear transaction. Because the company's reporting currency is USD, depreciation of the euro before settlement could reduce the dollar value of the receivable and negatively affect projected cash flows.

At the November 19 reference exchange rate of 1.0992 USD/EUR, the receivable has an estimated value of $11,541,600. Every $0.01 decrease in the EUR/USD exchange rate reduces the unhedged proceeds by $105,000.

The objective of this analysis is to identify a hedging strategy that protects the company's cash flows while considering financial costs, liquidity requirements, and potential benefits from favorable exchange-rate movements. For this recommendation, I assume that management prioritizes cash-flow stability and budget certainty over speculative gains.

## B. Hedge Outcomes

The following results summarize the modeled settlement-date proceeds using the November 19 market inputs and retained scenario assumptions.

| Strategy | Baseline USD Proceeds | Minimum USD Proceeds |
|---|---:|---:|
| Forward hedge | $12,397,350.00 | $12,397,350.00 |
| Money-market hedge | $11,721,307.56 | $11,721,307.56 |
| Put option hedge | $11,272,299.98 | $11,272,299.98 |
| Unhedged | $11,541,600.00 | No contractual floor |

### Forward Hedge

The forward hedge provides the highest guaranteed proceeds under the supplied inputs. At the assigned forward rate of 1.1807 USD/EUR, the company would receive $12,397,350 at settlement.

This exceeds the baseline unhedged proceeds by $855,750 and the money-market hedge by $676,042.44. The forward also avoids an upfront option premium and eliminates uncertainty regarding the exchange rate applied to the receivable.

Its primary disadvantage is that the company cannot benefit from EUR appreciation beyond the contracted forward rate. Additionally, the assigned bank quote must be confirmed before execution.

### Money-Market Hedge

The money-market hedge provides fixed settlement proceeds of $11,721,307.56. It protects the company from unfavorable exchange-rate movements by borrowing euros, converting them into USD, and investing the proceeds until settlement.

Although this strategy provides exchange-rate certainty, it generates lower proceeds than the assigned forward contract. It also requires access to EUR borrowing and USD investment facilities, potentially increasing administrative complexity and affecting the company's borrowing capacity.

The money-market hedge remains a reasonable alternative if the assigned forward quote is unavailable.

### Put Option Hedge

The EUR put option establishes minimum net proceeds of $11,272,299.98 while allowing the company to benefit from favorable EUR appreciation.

However, the option requires an upfront premium of $257,250, equivalent to a settlement-date cost of $269,300.02. This reduces the company's guaranteed proceeds and creates an immediate liquidity requirement.

The put option is most appropriate when management places substantial value on retaining exchange-rate upside. Under the supplied inputs, its flexibility does not outweigh the forward hedge's higher guaranteed proceeds.

### Unhedged Position

Remaining unhedged avoids contractual commitments, borrowing arrangements, and option premiums. However, it leaves the company fully exposed to exchange-rate fluctuations.

A 5% depreciation of the euro would reduce settlement proceeds to $10,964,520, representing a $577,080 decline from the baseline value. This uncertainty could negatively affect budgeting and the company's ability to meet planned USD obligations.

### Call Option

The purchased EUR call option was evaluated as a reference calculation. At the baseline settlement rate, its standalone net payoff is negative $492,434.32.

A EUR call primarily protects a EUR payable against appreciation. Because the company holds a EUR receivable and faces depreciation risk, purchasing a call would not provide the required downside protection. Therefore, it is excluded from the recommended receivable hedging strategies.

## C. Sensitivity Interpretation

The sensitivity analysis evaluates 11 settlement exchange-rate scenarios ranging from 5% EUR depreciation to 5% EUR appreciation.

| Strategy | EUR Depreciation (-5%) | Baseline (0%) | EUR Appreciation (+5%) |
|---|---:|---:|---:|
| Forward | $12,397,350.00 | $12,397,350.00 | $12,397,350.00 |
| Money-market | $11,721,307.56 | $11,721,307.56 | $11,721,307.56 |
| Put option | $11,272,299.98 | $11,272,299.98 | $11,849,379.98 |
| Unhedged | $10,964,520.00 | $11,541,600.00 | $12,118,680.00 |

The forward and money-market hedges maintain constant proceeds across all settlement exchange rates. This makes both strategies suitable for a company that prioritizes financial planning and predictable cash flows.

The put option protects against significant EUR depreciation while retaining appreciation benefits. However, its premium reduces the net proceeds, even when exchange rates move favorably.

The unhedged position provides full participation in EUR appreciation but also exposes the company to the greatest downside risk.

Under the supplied assumptions, the forward hedge produces the highest proceeds in all 11 sensitivity scenarios. Even with 5% EUR appreciation, the forward produces $278,670 more than the unhedged position and $547,970.02 more than the put option.

The unhedged position would outperform the forward only if the settlement exchange rate exceeded 1.1807. The put option would outperform the forward only above approximately 1.206348 USD/EUR, representing approximately 9.75% appreciation from the initial spot rate.

These thresholds demonstrate the potential opportunity cost of the forward hedge. However, the sensitivity scenarios are not exchange-rate forecasts, and the available information does not establish the probability of appreciation beyond these levels.

## D. Recommendation

I recommend hedging 100% of the EUR 10,500,000 receivable through a 365-day forward contract, subject to confirmation that the assigned forward rate of 1.1807 USD/EUR is executable.

This strategy provides the highest modeled guaranteed proceeds of $12,397,350 and outperforms the other receivable strategies throughout the prescribed sensitivity range. It also avoids the upfront premium associated with options and the borrowing requirements of a money-market hedge.

### Covered Interest Parity Assessment

The assigned bank forward quote does not agree with the forward rate implied by covered interest parity (CIP).

| Measurement | Result |
|---|---:|
| Assigned bank forward rate | 1.180700 USD/EUR |
| CIP-implied forward rate | 1.116315 USD/EUR |
| Rate difference (CIP minus bank quote) | -0.064385 USD/EUR |
| Absolute percentage deviation | 5.4531% |
| USD impact on receivable (CIP minus bank quote) | -$676,042.44 |
| Model parity status | REVIEW |

The discrepancy is economically significant and exceeds the model's permitted tolerance of 0.05%.

Several factors may explain this difference. The assigned forward quote does not have a documented market timestamp, while the spot and interest-rate inputs reflect the November 19 market-data assumptions. Additionally, the ECB reference rate is not an executable spot quote, and government bond yields are proxies rather than actual corporate borrowing and investment rates.

These differences in timing, pricing conventions, and financing conditions may explain why the assigned forward rate differs from the theoretical rate. The discrepancy should not be interpreted as evidence of an executable arbitrage opportunity.

The parity discrepancy does not change my preferred hedging instrument, but it makes the recommendation conditional. If the bank confirms the assigned forward rate, the company should proceed with the forward hedge.

If the bank instead offers a forward rate near the CIP-implied rate of 1.116315, the expected proceeds would decrease to approximately $11,721,307.56, eliminating the modeled financial advantage over the money-market hedge.

In that case, management should compare updated executable forward quotes, borrowing rates, investment rates, and option premiums before committing to a transaction.

## E. Executive Justification

### Cash-Flow Stability and Budget Certainty

The forward hedge allows the company to establish a predictable USD cash inflow. This supports budgeting, operational planning, and the management of future USD-denominated obligations.

Given the size of the receivable, reducing exchange-rate uncertainty is more valuable under the assumed risk posture than retaining speculative upside.

### Liquidity and Financing Requirements

Unlike the put option, the forward does not require an upfront option premium. Unlike the money-market hedge, it does not require the company to borrow EUR and invest USD.

This makes the forward operationally simpler and potentially less demanding on existing financing resources. However, any collateral requirements, credit limits, or other contractual obligations should be confirmed with the bank.

### Flexibility and Opportunity Cost

The forward eliminates the opportunity to benefit from EUR appreciation beyond the contracted rate. Nevertheless, the supplied forward rate is sufficiently favorable that the company would need substantial EUR appreciation before the unhedged position or put option produces higher proceeds.

Under the assumed preference for predictable cash flows, accepting this opportunity cost is justified.

### Implementation

Before executing the hedge, management should:

1. Obtain a binding forward quote covering the full EUR 10,500,000 receivable for the required settlement date.
2. Confirm that the quote is expressed in USD/EUR and review applicable fees, collateral requirements, and credit terms.
3. Obtain comparable executable EUR borrowing and USD investment rates.
4. Recalculate the alternatives if the confirmed forward quote differs materially from the assigned rate.
5. Execute the selected hedge after confirming that the amount and maturity match the underlying receivable.

## Conclusion

The forward hedge provides the strongest combination of modeled financial proceeds, cash-flow stability, budget certainty, and operational simplicity.

Subject to confirmation of the assigned bank quote, hedging the entire receivable through a forward contract is the recommended strategy.

The covered interest parity discrepancy remains the principal implementation concern. Management should resolve this issue through executable market quotations before entering into the contract.

## Supporting Documents

- [Stage 2 — FX Hedging Specification](../../capabilities/fx-hedging/spec.md)
- [Stage 4 — Market Data Memo](../../data/2026-11-19-landing-gear-market-data-memo.md)
- [Excel Hedging Model](../../capabilities/fx-hedging/model.xlsx)
- [Stage 5 — Validation Analysis](../../analysis/2026-11-27-landing-gear-validation-analysis.md)
- [Independent LLM Output](../../analysis/2026-11-27-landing-gear-independent-llm-output.md)
