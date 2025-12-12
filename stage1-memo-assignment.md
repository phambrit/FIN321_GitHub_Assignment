# FX Risk Exposure & Hedging Strategy: EUR Receivable

**Author:** Britney Pham  
**Course:** FIN 312  
**Version:** 1.0  
**Date Created:** October 24, 2025  
**Last Updated:** October 24, 2025  

---

## Executive Summary

The firm faces a **€4,500,000 EUR-denominated receivable in one year** from a European customer. With the current 1-year EUR/USD forward rate at **1.0875**, the USD value of this receivable is exposed to adverse movements in the euro. A depreciation of the EUR would reduce dollar proceeds and negatively affect revenue forecasts.

This memo explains why hedging the exposure is prudent, introduces three primary FX hedge families, and outlines the methodology for evaluating them. A spreadsheet-based model will compare unhedged outcomes with forward contracts, money market hedges, and options. The objective is to recommend an optimal strategy that balances **risk reduction, cost, and upside potential**.

---

## Background & Objectives

The company expects to receive **€4.5 million in one year**, which at the current forward rate of 1.0875 equates to approximately **$4.893 million**. However, any depreciation of the euro over the next 12 months would reduce the USD value of this receivable.

This FX exposure directly impacts reported revenue, budgeting accuracy, and cash flow planning. The objective of this analysis is to:

- Quantify the FX risk associated with the receivable  
- Evaluate three primary hedging approaches  
- Compare protection, cost, and flexibility across strategies  

The ultimate goal is to protect earnings while allowing management to make an informed hedging decision.

---

## Methods

### Hedge Families and Trade-Offs

#### Forward Contract
Locks in a fixed EUR/USD rate of **1.0875** for delivery in one year.

**Pros**
- Full protection against EUR depreciation  
- No upfront cost  

**Cons**
- No upside participation if the EUR appreciates  

---

#### Money Market Hedge
Uses borrowing and lending in EUR and USD markets to synthetically lock in value today.

**Pros**
- Locks in value using interest rate parity  
- Effective for firms with balance sheet flexibility  

**Cons**
- Requires actual cash transactions  
- More complex to execute and monitor  

---

#### Currency Options (EUR Put Option)
Purchases the right to sell EUR at a fixed exchange rate.

**Pros**
- Downside protection with upside potential  
- Strategic flexibility  

**Cons**
- Upfront premium cost (**$0.015 per EUR**)  

---

### Technical Specification

The analysis will be implemented using an Excel-based model that:

- Compares USD outcomes across multiple EUR/USD spot rate scenarios  
- Evaluates:
  - Unhedged exposure  
  - Forward hedge  
  - Money market hedge  
  - EUR put option hedge  

**Key Inputs**
- Spot exchange rate  
- Forward exchange rate  
- USD and EUR interest rates  
- Option premiums  

**Key Outputs**
- Net USD proceeds under each hedging strategy  

---

## Prompt Engineering (Model Generation)

The spreadsheet model can be generated using the following prompt:

> *“Given a €4.5M receivable in one year, current spot and forward EUR/USD rates, USD and EUR interest rates, and option premiums, build a spreadsheet that compares USD proceeds under: (1) unhedged exposure, (2) forward contract, (3) money market hedge, and (4) EUR put option hedge. Include scenario analysis for varying EUR/USD spot rates at maturity.”*

---

## Limitations & Next Steps

### Limitations
- Interest rates and option prices may change over time  
- Assumes no counterparty default risk  
- Ignores transaction costs and market frictions  

### Next Steps
- Build the Excel model  
- Gather current market interest rate data  
- Run scenario analysis and recommend a hedge in Stage 3  

---

## References

- Investopedia. *Foreign Exchange Hedging*  
- Hull, J. (2021). *Options, Futures, and Other Derivatives* (11th ed.)  
- Yahoo Finance (EUR/USD spot and forward rates)
