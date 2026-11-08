# Samantha-Guo
My finance and economics portfolio
## About Me

Hello! My name is **Samantha Guo**, and I am an undergraduate student pursuing a Bachelor of Business Administration in Accounting at the **Shidler College of Business, University of Hawaiʻi at Mānoa**. I have a strong interest in accounting, finance, economics, and international business. Through my academic experiences, I have developed an appreciation for how financial information and economic principles influence business decisions.

In Spring 2026, I had the opportunity to study abroad at **Shanghai Jiao Tong University in China**, where I expanded my understanding of international business, strategic management, and economics. Studying in a different academic and cultural environment strengthened my adaptability, cross-cultural communication, and global perspective. I also completed a **Solutions Internship at KMH LLP** in Honolulu, where I gained practical experience with accounting, auditing procedures, internal controls, and financial reporting.

Beyond accounting, I am particularly interested in **international finance, financial analysis, business strategy, and global economic trends**. I enjoy exploring how businesses operate across different markets, how financial decisions affect organizational performance, and how economic conditions shape business opportunities. I am continuously looking for opportunities to expand my analytical, technical, and problem-solving skills.

As I approach graduation, my goal is to pursue a career that allows me to apply my accounting and financial knowledge while continuing to learn and grow professionally. I am also interested in exploring opportunities in international business and finance. Through this portfolio, I hope to showcase my **academic projects, professional experiences, analytical skills, and personal development** as I continue building my career.

# FX Hedging — Scenario 15: Landing Gear

## Project Overview

This project develops an Excel-based foreign exchange hedging model for a company expecting to receive €10,500,000 in 365 days.

The objective is to compare three hedging strategies—forward contract, money-market hedge, and EUR put option—against the unhedged position to evaluate their effects on USD proceeds.

## Hedging Strategies

- **Forward Hedge:** Locks in a fixed USD amount using an agreed forward exchange rate.
- **Money-Market Hedge:** Borrows euros today, converts them into USD, and invests the dollars until settlement.
- **Put Option Hedge:** Protects against euro depreciation while allowing the company to benefit from euro appreciation, after accounting for the option premium.

## Project Stages

1. **Stage 1 — Executive Brief:** Explain the foreign exchange exposure and available hedging strategies.
2. **Stage 2 — Model Specification:** Define workbook inputs, formulas, architecture, assumptions, sensitivity analysis, validation rules, and outputs.
3. **Stage 3 — AI-Assisted Build and Audit:** Construct and test the Excel workbook using the specification.
4. **Stage 4 — Market Data and Population:** Obtain and document market data to populate the workbook.
5. **Stage 5 — Validation and Decision Memo:** Validate the model and recommend a hedging strategy.

## Current Status

Stage 1: Executive brief completed.

Stage 2: Model specification drafted, reviewed, and revised.

Stages 3–5: Not yet completed.

## Project Files

- `spec.md` — Detailed workbook design and calculation requirements.
- `README.md` — Project overview and progress.
- `../../prompt-log.md` — Documentation of AI assistance, review feedback, and revisions.

## Model Design

The planned workbook will contain eight worksheets and compare four outcomes: unhedged, forward hedge, money-market hedge, and put option hedge.

The sensitivity analysis will evaluate 11 EURUSD settlement exchange rates, from 5% below to 5% above the initial spot rate.

All market-dependent placeholder inputs will be verified or replaced with sourced market data during Stage 4.

## Tools

- GitHub — Version control and project documentation.
- ChatGPT — Assistance with specification drafting, review, and revisions.
- Microsoft Excel — Planned workbook construction and financial analysis.
