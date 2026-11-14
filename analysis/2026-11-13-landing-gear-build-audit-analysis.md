# Stage 3 — FX Hedging Workbook Build Audit

**Scenario:** 15 — Landing Gear  
**Audit Date:** November 13, 2026  
**Project:** FX Hedging — AI-Assisted Build and Audit  
**Workbook:** `capabilities/fx-hedging/model.xlsx`  
**Specification:** `capabilities/fx-hedging/spec.md`

## 1. Audit Objective

The purpose of this audit was to determine whether the AI-generated Excel workbook followed the requirements established in the Stage 2 specification.

I manually reviewed the workbook in Microsoft Excel, checking named ranges, formulas, hedge calculations, sensitivity analysis, formatting, and validation results.

## 2. Audit Findings

### Finding 1 — Named Range Integrity

**What I checked:** I opened Excel's Name Manager and inspected the ten required input names.

**What I found:** All ten named ranges were present and correctly linked to their corresponding input cells.

**What I did:** Confirmed that the names matched the Stage 2 specification. No corrections were necessary.

**Status:** PASS

### Finding 2 — Forward Hedge Formula

**What I checked:** I inspected the forward hedge proceeds cell to determine whether it used a formula rather than a hard-coded number.

**What I found:** The formula referenced `FC_AMT` and `F0_in`, producing $12,397,350.00.

**What I did:** Compared the result with the specification's validation figure and confirmed it matched.

**Status:** PASS

### Finding 3 — Money-Market Hedge and Parity

**What I checked:** I reviewed the three money-market hedge steps and the covered interest rate parity validation.

**What I found:** The borrowing, conversion, and investment calculations used formulas and matched the specification's expected results. The parity status displayed REVIEW.

**What I did:** Retained the parity warning because the initial inputs are indicative. I did not adjust the rates simply to make the validation pass. The market inputs will be reviewed in Stage 4.

**Status:** PASS — Parity REVIEW

### Finding 4 — Put and Call Option Calculations

**What I checked:** I inspected the put premium, financed premium cost, protected minimum proceeds, and call option calculations.

**What I found:** The initial put premium was $257,250.00. The financed premium was treated as a cost, the protected floor matched the specification, and the call calculations were present.

**What I did:** Confirmed the premium signs and formulas. No correction was required.

**Status:** PASS

### Finding 5 — Sensitivity Recalculation

**What I checked:** I changed `S0_in` from 1.1800 to 1.2000 and inspected the sensitivity table and chart.

**What I found:** The table and chart updated correctly. The −5%, 0%, and +5% settlement rates became 1.1400, 1.2000, and 1.2600. Forward proceeds remained $12,397,350.00.

**What I did:** Restored `S0_in` to 1.1800 after the test.

**Status:** PASS

### Finding 6 — Workbook Structure and Validation

**What I checked:** I inspected the eight worksheets, color conventions, cover information, and validation checks.

**What I found:** All eight worksheets were present, formatting followed the required conventions, and the validation checks displayed their expected results without visible Excel formula errors.

**What I did:** Confirmed that the reviewed workbook elements matched the build requirements.

**Status:** PASS

## 3. Specification Defect Identified and Corrected

Before generating the workbook, I identified that Section 1, Problem Statement, was missing from my Stage 2 specification.

I corrected the specification by adding the problem statement, exposure information, hedging alternatives, and model objective.

I committed this correction to GitHub before proceeding with the workbook build.

## 4. Outstanding Issues and Limitations

The workbook uses indicative and placeholder market inputs that will be verified or replaced in Stage 4.

The covered interest rate parity check currently displays REVIEW because the initial rates do not satisfy the model's 0.05% tolerance. This warning is retained for further investigation.

The six manual audit tests did not identify calculation defects. A comprehensive automated formula-integrity check has not yet been documented.

## 5. Audit Conclusion

The six manual audit tests confirmed that the reviewed workbook elements followed the Stage 2 specification.

The named ranges, hedge calculations, sensitivity table, chart, and visible validation checks behaved as expected.

The workbook is ready for further integrity verification and Stage 4 market-data population.
