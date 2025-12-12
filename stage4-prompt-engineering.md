# Stage 4 – AI Excel Generation Prompt (FX Hedging Model)

## GOAL
Create a fully functional Excel (.xlsx) spreadsheet that models **forward**, **money market**, and **option** hedges for a EUR-denominated receivable.  
The model must strictly follow named-range conventions, color-coding rules, formatting requirements, and verification procedures.

---

## CONTEXT
This prompt translates the Stage 2 specification and Stage 3 Excel logic into a **precise, executable AI instruction** capable of generating a complete, professional FX hedging model.

Prompt-engineering best practices applied:
- Hierarchical structure
- Explicit variable definitions
- No inferred values
- Consistent named ranges
- Explicit formatting and color rules
- Clear verification and export instructions

---

## INPUT VARIABLES (USE EXACT VALUES)

All inputs must be **hard-coded**, **explicitly stated**, and assigned to named ranges.

### Exposure
- **FC_AMT = 4,500,000**  
  *EUR receivable*

### FX Rates (USD per EUR, Dec 10, 2025)
- **S0_in = 1.1634**  
  *Spot EURUSD*
- **F0_in = 1.0875**  
  *1-year forward EURUSD*

### Interest Rates (Simple annual basis)
- **R_USD = 0.0363**  
  *U.S. 1-year rate*
- **R_FC = 0.02268**  
  *EUR 1-year rate*

### Options (per EUR)
- **K_PUT = 1.1634**
- **K_CALL = 1.1634**
- **PREM_PUT = 0.015**
- **PREM_CALL = 0.018**

### Time Convention
- **T_DAYS = 360**
- **T_YRS = 1.0**

The AI must not infer or fetch values.  
All values above must appear in the Excel input section.

---

## SPREADSHEET REQUIREMENTS

### SHEETS
Create the following worksheets:
1. `Inputs_Summary`
2. `Scenarios`
3. `Audit_Map`

---

## NAMED RANGE DEFINITIONS

The following named ranges **must exist exactly as written**:

- `FC_AMT`
- `S0_in`
- `F0_in`
- `R_USD`
- `R_FC`
- `K_PUT`
- `K_CALL`
- `PREM_PUT`
- `PREM_CALL`
- `T_DAYS`
- `T_YRS`

No alternative naming conventions are allowed.

---

## FORMATTING & COLOR CODING

Apply these colors consistently across all sheets:

- **Yellow** — Inputs / decision variables  
- **Blue** — Assumptions  
- **Green** — Formula cells  
- **Gray** — Outputs / KPIs  

All named-range input cells must be yellow.  
All calculated cells must be green.

---

## MODEL LOGIC (PSEUDOCODE)

### Scenario Spot Rates
S_T = sequence(0.95 * S0_in , 1.05 * S0_in , step = 0.01)

### Unhedged Exposure
USD_unhedged = FC_AMT * S_T

### Forward Hedge
USD_forward = FC_AMT * F0_in

### Money Market Hedge (3-Step)
EUR_borrow     = FC_AMT / (1 + R_FC * T_YRS)
USD_invest_0   = EUR_borrow * S0_in
USD_MM         = USD_invest_0 * (1 + R_USD * T_YRS)

### Put Option Hedge
Premium_PUT_total = FC_AMT * PREM_PUT
Payoff_PUT        = max(K_PUT - S_T, 0) * FC_AMT

USD_PUT_SCEN =
if S_T < K_PUT:
FC_AMT * K_PUT - Premium_PUT_total
else:
FC_AMT * S_T - Premium_PUT_total

### Call Option Hedge
Premium_CALL_total = FC_AMT * PREM_CALL
Payoff_CALL        = max(S_T - K_CALL, 0) * FC_AMT

USD_CALL_SCEN =
(FC_AMT * S_T + Payoff_CALL) - Premium_CALL_total

---

## MODEL COMPONENTS

### Required Calculations
- Unhedged exposure
- Forward hedge
- Money market hedge
- Put option hedge
- Call option hedge

### Scenario Table
For each `S_T`, include:
- `USD_unhedged`
- `USD_forward`
- `USD_MM`
- `USD_PUT_SCEN`
- `USD_CALL_SCEN`

---

## SENSITIVITY ANALYSIS
Create a sensitivity table showing USD outcomes across the ±5% spot-rate range (0.95×S0_in to 1.05×S0_in).

---

## OUTPUT REQUIREMENTS

On `Inputs_Summary`, display gray KPI outputs for:
- Unhedged baseline (S_T = S0_in)
- Forward hedge proceeds
- Money market hedge proceeds
- Put hedge proceeds (baseline)
- Call hedge proceeds (baseline)

---

## CHARTS
Create a line chart plotting USD proceeds vs. `S_T` for:
- Unhedged
- Forward
- Money market
- Put hedge
- Call hedge

---

## VERIFICATION

Before exporting the file, confirm:

1. **Interest Rate Parity**
F0_in ≈ S0_in × (1 + R_USD × T_YRS) / (1 + R_FC × T_YRS)

2. **Forward ≈ Money Market hedge results**

3. **All named ranges exist in Name Manager**

4. **Audit_Map sheet lists**
   - Named range
   - Cell address
   - Description
   - Formula dependencies

---

## EXPORT
Return a downloadable **Excel (.xlsx) file** that meets all requirements above.

---

# Deliverable 2 — Fully Functional Excel Workbook Generated with the Prompt
https://github.com/phambrit/FIN321_GitHub_Assignment/blob/main/Stage4_Deliverable2.xlsx
