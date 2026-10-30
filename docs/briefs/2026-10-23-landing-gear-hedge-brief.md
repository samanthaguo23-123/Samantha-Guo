---
type: brief
engagement: fx-hedging
capability: fx-hedging
date: 2026-10-23
status: committed
hypothesis: "REPLACE WITH YOUR OWN PREDICTION"
---

# FX Hedging Executive Brief
## Scenario 15 — Landing Gear

**To:** Chief Financial Officer  
**From:** Samantha Guo  
**Subject:** Managing EUR Receivable Exchange-Rate Risk

## Exposure and Business Risk

A U.S. landing-gear manufacturer has invoiced a French aircraft manufacturer for EUR 10,500,000, payable in 365 days. Although the euro receivable is fixed, its U.S.-dollar value is not. If the euro weakens against the dollar before collection, the company will convert the payment into fewer dollars, reducing cash available for operating expenses and potentially compressing margins.

For illustration, at EURUSD 1.20 the receivable would yield $12,600,000, while at 1.10 it would yield $11,550,000—a $1,050,000 difference. These rates illustrate sensitivity; they are not current market quotations.

## Hedging Alternatives

Three hedging approaches merit evaluation.

Forward contract: A forward contract would lock in the exchange rate for selling euros in 365 days. At the assigned indicative rate of 1.1807 USD/EUR, the contract would secure approximately $12,397,350 before any transaction costs. This provides budget certainty, but the company would forgo additional dollar proceeds if the euro appreciates.

Money-market hedge: A money-market hedge could create a similar locked-in dollar amount by borrowing the present value of the euro receivable today, converting those euros to dollars at the current spot rate, and investing the dollars until collection. The eventual euro payment would repay the euro loan. This strategy may be competitive with the forward, but it consumes borrowing capacity and depends on available USD and EUR interest rates.

Currency put option: The company could buy a put option giving it the right to sell euros at a predetermined strike, set at spot under the assigned scenario. This would establish a minimum conversion rate while preserving the benefit of a stronger euro. However, the put costs $0.0245 per euro, or $257,250 for the full receivable, before considering financing of the premium. The option's net outcome must therefore account for that cost.

## Assumptions and Hypothesis

For this preliminary assessment, I assume the customer pays the full EUR 10,500,000 on schedule, the exposure is not naturally offset by euro expenses, and the quoted instruments can be obtained in the required size and maturity. Actual spot rates, interest rates, credit terms, and transaction costs must be verified before comparing alternatives.

My hypothesis is that the forward will provide a higher guaranteed net dollar outcome than the put option's protected minimum because the option requires a $257,250 premium, although the put may outperform if the euro appreciates sufficiently.

This hypothesis would be challenged if the put's net floor exceeds the forward proceeds after realistic costs, or if observed market inputs materially change the comparison. The money-market hedge could also prove preferable if its locked-in proceeds exceed the forward's.
## Proposed Next Steps
The next step is to specify a workbook with clearly identified inputs, formulas, and validation checks (Stage 2). I will then use AI to build the workbook and independently audit its calculations (Stage 3), replace placeholders with sourced, timestamped market data (Stage 4), and verify results through manual checks and an independent AI comparison before presenting a final recommendation (Stage 5).

No hedge is recommended at this stage; the purpose of this brief is to establish the exposure and an evidence-based evaluation plan.
