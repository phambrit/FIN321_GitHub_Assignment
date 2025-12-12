# FX Hedging Model for EUR Receivable

**Author:** Britney Pham  
**Role:** Financial Analyst / Treasury Analyst  
**Audience:** CFO, Director of Treasury  
**Version:** 1.0  
**Last Updated:** November 7, 2025  

---

## 1. Problem Statement

The firm expects to receive a **€4,500,000 EUR-denominated payment in 12 months** for solar equipment exports. This creates **foreign exchange (FX) exposure** due to potential fluctuations in the EUR/USD exchange rate.

If the euro depreciates over the next year, the USD value of the receivable will decrease, negatively impacting revenue and earnings forecasts.

This specification defines the analytical framework for evaluating and comparing three FX hedging strategies:

- Forward contracts  
- Money market hedges  
- Currency options  

The objective is to identify a strategy that balances **cost, certainty, and upside potential** while preserving the USD value of the receivable.

---

## 2. Inputs (Known Variables)

| Variable        | Description                               | Unit      | Example / Source        |
|-----------------|-------------------------------------------|-----------|-------------------------|
| `FC_AMT`        | Foreign currency receivable               | EUR       | 4,500,000 (Internal)    |
| `S0`            | Current EUR/USD spot rate                 | USD/EUR   | Look up (Market)        |
| `F0`            | 1-year EUR/USD forward rate               | USD/EUR   | 1.0875 (Provided)       |
| `r_USD`         | USD 1-year interest rate                  | %         | Look up (Market)        |
| `r_EUR`         | EUR 1-year interest rate                  | %         | Look up (Market)        |
| `t`             | Time to maturity                          | Years     | 1                       |
| `K_put`         | EUR put option strike price               | USD/EUR   | = S0                    |
| `K_call`        | EUR call option strike price              | USD/EUR   | = S0                    |
| `Premium_put`  | EUR put option premium (paid upfront)     | USD       | 0.015 (Provided)        |
| `Premium_call` | EUR call option premium (paid upfront)    | USD       | 0.018 (Provided)        |

---

## 3. Assumptions & Constraints

- Interest rates are quoted on a **simple annual basis** (360-day convention).
- Forward rate maturity aligns exactly with the receivable timing.
- Options are **European-style** with 1-year maturity.
- Option premiums are paid upfront in USD.
- No transaction costs, taxes, or counterparty credit risk are considered.
- Exchange rates are quoted as **USD per EUR**.
- Option strikes are set **at-the-money (ATM)** for analysis.

---

## 4. Calculation Flow

USD_forward = FC_AMT × F0

---

### 4.2 Money Market Hedge

1. Borrow the present value of the EUR receivable at `r_EUR`.
2. Convert borrowed EUR to USD at the spot rate `S0`.
3. Invest USD proceeds at `r_USD` for one year.

Final USD proceeds:

USD_mm = (FC_AMT / (1 + r_EUR)) × S0 × (1 + r_USD)

---

### 4.3 Options Hedge

#### Put Option (Downside Protection)

- Premium paid upfront.
- If `S_T < K_put`, exercise the option:

USD_put = FC_AMT × K_put − Premium_put

- If `S_T ≥ K_put`, let the option expire and convert at spot:

USD_put = FC_AMT × S_T − Premium_put

#### Call Option (Upside Participation)

- Modeled symmetrically to capture upside beyond the strike price.

---

### 4.4 Unhedged Exposure

USD value at maturity without hedging:

USD_unhedged = FC_AMT × S_T

---

### 4.5 Strategy Comparison

- Compare USD proceeds across:
  - Forward hedge
  - Money market hedge
  - Options hedge
  - Unhedged position
- Evaluate:
  - Certainty
  - Liquidity impact
  - Cost of hedging
  - Upside participation

---

## 5. Outputs

| Output Name        | Description                                  | Format      | Purpose                          |
|--------------------|----------------------------------------------|-------------|----------------------------------|
| `USD_forward`      | Forward hedge proceeds                        | Numeric     | Certainty benchmark              |
| `USD_mm`           | Money market hedge proceeds                  | Numeric     | Interest parity validation       |
| `USD_put`          | Put option proceeds across scenarios         | Table       | Downside protection analysis     |
| `USD_call`         | Call option proceeds across scenarios        | Table       | Upside participation analysis    |
| `USD_unhedged`     | Unhedged exposure at future spot rates       | Table       | Baseline risk profile            |
| `Chart_1`          | USD proceeds vs. EUR/USD at maturity         | Line chart  | Strategy comparison              |
| `Summary`          | Written evaluation and recommendation        | Paragraph   | Executive decision support       |

---

## 6. Sensitivity Plan

- Vary future spot rate `S_T` from **0.95 × S0 to 1.05 × S0**.
- Increment by **0.01**.
- Compute USD proceeds for:
  - Unhedged position
  - Forward hedge
  - Money market hedge
  - Options hedge
- Display results in:
  - A summary table
  - A multi-line comparison chart
- Identify breakeven points and risk–reward trade-offs.

---

## 7. Limitations & Next Steps

### Limitations
- Does not incorporate FX volatility or implied volatility.
- Assumes frictionless markets and perfect execution.
- Ignores transaction costs and counterparty risk.

### Next Steps
- Implement this logic in a fully functional Excel model.
- Label variables clearly for AI-based spreadsheet generation.
- Perform scenario analysis and produce executive recommendations.
