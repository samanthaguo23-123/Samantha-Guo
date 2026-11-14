# AI Prompt Log

This file documents meaningful AI-assisted work on my finance and economics portfolio. Each entry records the task, AI assistance, verification, and corrections. Entries are added as sessions occur, not reconstructed later.

## 2026-10-08 — GitHub Portfolio Setup

**AI tool:** ChatGPT (OpenAI)

**Task:** Set up my public GitHub portfolio according to the Stage 0 requirements.

**AI assistance:**
- Explained the GitHub repository setup process step by step.
- Helped prepare starter content for AGENTS.md, CLAUDE.md, and .gitignore.
- Converted my existing resume into Markdown format for RESUME.md.
- Helped prepare this prompt log.

**My responsibility and verification:**
- Created the GitHub account and repository.
- Wrote my own README.md biography.
- Reviewed and committed the required files.
- [Add any specific checks or corrections I made.]

**Errors or limitations:**
- [Record any errors found, or write 'None identified' after checking.]

**Outcome:** Portfolio setup in progress; remaining folder structure and collaborator invitation still need completion.

## 2026-10-29 — FX Hedging Stage 1: Executive Brief

**AI Tool:** ChatGPT (OpenAI)

**Task:** Help me understand the Stage 1 requirements and prepare a 400–600-word executive brief for my assigned Landing Gear scenario.

**Prompts Used:**
- "Teach me step by step what to do."

**How AI Was Used:**
- Helped me understand the assignment instructions and what needed to be included.
- Explained the differences between forward contracts, money-market hedges, and currency options.
- Provided calculations for the forward contract and put option premium using my assigned scenario.

**Verification and Human Review:**
- Reviewed the AI-generated draft to understand the explanations and calculations.
- Identified the assigned scenario values used in the calculations.
- Independently checked the calculations and confirm the final word count.

**Limitations or Errors:**
- Current EURUSD spot and USD/EUR interest rates have not yet been researched or verified.
- The forward rate is indicative, and the comparison does not yet include all financing and transaction costs.

**Outcome:** Prepared an AI-assisted draft of the Stage 1 executive brief and received instructions for organizing the FX hedging project in GitHub.

## FX Hedging Stage 2 — AI Review and Revision

**Project:** Scenario 15 — Landing Gear  
**File reviewed:** `capabilities/fx-hedging/spec.md`

### Initial Draft

I prepared a model specification describing the inputs, workbook architecture, assumptions, formulas, sensitivity analysis, validation checks, and expected outputs for an FX hedging workbook.

I used ChatGPT to help draft and organize the specification, then submitted the draft for an additional review before building the Excel model.

### AI Review Prompt

"Review my FX hedging model specification against the Stage 2 assignment requirements. Identify missing sections, calculation errors, incomplete formulas, and unclear instructions that could cause problems when building the Excel workbook in Stage 3."

### AI Feedback

The review identified several issues:

1. Section 5.6 needed clarification that the call option calculation applies to a foreign-currency payable, not the EUR receivable being hedged.
2. Section 6.4 contained an incomplete sentence about settlement-date proceeds.
3. Section 7.2 needed more precise money-market calculation checkpoints.
4. Section 7.5 was incomplete and needed additional sensitivity and workbook integrity checks.
5. Section 8 needed a complete description of the named outputs, summary table, sensitivity table, chart, and validation results.

### Revisions Made

I revised the specification to clarify the call option's purpose, complete the sensitivity assumptions, improve the money-market validation figures, add workbook integrity checks, and define the required outputs more precisely.

I also clarified that the baseline output names refer to calculations at the initial spot rate, while the sensitivity table calculates results separately for each settlement-rate scenario.

### What I Learned

The review showed me why a model specification needs precise formulas, consistent named ranges, and clear validation requirements. Small ambiguities in a written specification can lead to incorrect formulas or outputs when an AI builds the Excel workbook.

The revised specification will serve as the instructions for constructing and auditing the workbook in Stage 3.
## Stage 3 — AI-Assisted Workbook Build and Audit

**Date:** November 13, 2026  
**Scenario:** 15 — Landing Gear  
**AI Tool:** ChatGPT

### Prompt 1 — Workbook Generation

**Task:** Generate an Excel workbook based on the committed Stage 2 specification.

**Instructions provided:** Build a working FX hedging workbook from `capabilities/fx-hedging/spec.md`, including all ten required named ranges, formula-driven calculations, eight worksheets, forward and money-market hedges, put and call option calculations, an 11-scenario sensitivity table, a chart, and validation checks.

**AI Output:** An Excel workbook named `model.xlsx` was provided for review.

**Human Review:** Opened the workbook in Microsoft Excel and began auditing its structure and calculations against the specification.

### Prompt 2 — Formula and Calculation Audit

**Task:** Evaluate whether the AI-generated workbook followed the Stage 2 calculation requirements.

**AI Assistance:** ChatGPT provided a step-by-step audit checklist for the named ranges, forward hedge, money-market hedge, option calculations, and parity check.

**Human Review:** Confirmed that the ten named inputs were correctly assigned, the forward hedge produced $12,397,350.00, and the money-market hedge followed the three required steps. Confirmed that the parity check displayed REVIEW.

### Prompt 3 — Sensitivity and Integrity Audit

**Task:** Test whether the sensitivity table and chart recalculated when an input changed.

**AI Assistance:** ChatGPT provided a test using `S0_in = 1.2000`.

**Human Review:** Changed the spot rate from 1.1800 to 1.2000 and confirmed that the sensitivity table and chart updated. Verified that forward proceeds remained unchanged, then restored the original spot rate.

Also reviewed the eight worksheets, formatting, and visible validation checks.

### Prompt 4 — Audit Documentation

**Task:** Prepare a Stage 3 audit report documenting the workbook review.

**AI Output:** ChatGPT drafted a structured audit report containing six findings.

**Human Review:** Used the findings from the Excel inspection to document what was checked, what was found, and what actions were taken.

**Audit Report:** `analysis/2026-11-13-landing-gear-build-audit-analysis.md`

### Specification Correction

Before workbook generation, Section 1 (Problem Statement) was identified as missing from the Stage 2 specification.

The specification was updated and committed to GitHub before continuing the build.

### Remaining Limitations

The workbook contains indicative market inputs that require verification in Stage 4.

The parity check displays REVIEW because the placeholder inputs do not satisfy the model's tolerance. The warning was retained rather than forced to pass.

The manual audit did not identify additional calculation defects. A comprehensive automated formula-integrity check remains to be documented.
