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
