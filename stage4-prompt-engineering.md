GOAL

Create a fully-functional Excel file that models forward, money market, and option hedges for my EUR receivable.
The model must follow strict named-range usage, color-coding standards, formatting rules, and full verification steps.

⸻

CONTEXT

Translate the modeling logic from my Stage 2 specification and Stage 3 Excel logic into a new, complete, professional spreadsheet.
Follow the prompt-engineering best practices shown below:
	•	Use hierarchical structure
	•	Avoid vague instructions
	•	Provide all variable values explicitly
	•	Use named ranges consistently
	•	Specify formatting explicitly
	•	Include verification procedures

⸻

INPUT VARIABLES (Use These Exact Values)

These values must be hard-coded as yellow input cells and assigned to named ranges exactly as written.

Exposure
	•	FC_AMT = 4,500,000 (EUR receivable)

Market Data (real values as of Dec 10, 2025)
	•	S0_in = 1.1634 (EURUSD spot)
	•	F0_in = 1.0875 (1-year EURUSD forward)
	•	R_USD = 0.0363 (U.S. 1-year interest rate)
	•	R_FC = 0.02268 (EUR 1-year interest rate)

Options
	•	K_PUT = 1.1634
	•	K_CALL = 1.1634
	•	PREM_PUT = 0.015
	•	PREM_CALL = 0.018

Timing
	•	T_DAYS = 360
	•	T_YRS = 1.0

All numeric values must appear as explicit inputs.
AI must not infer or create values.

⸻

SPREADSHEET REQUIREMENTS

1. SHEETS

Create, at minimum, the following sheets:
	1.	Inputs_Summary
	2.	Scenarios
	3.	Audit_Map

2. NAMED RANGES

Assign the following names exactly:
	•	FC_AMT
	•	S0_in
	•	F0_in
	•	R_USD
	•	R_FC
	•	K_PUT
	•	K_CALL
	•	PREM_PUT
	•	PREM_CALL
	•	T_DAYS
	•	T_YRS

These must appear in the Name Manager and be used consistently in formulas.

3. COLOR CODING

Use these colors across all sheets:
	•	Yellow = Inputs / decision variables
	•	Blue = Assumptions
	•	Green = Formulas
	•	Gray = Outputs / KPIs

Do NOT deviate from this scheme.

4. MODEL COMPONENTS (Must Be Implemented Exactly)

(A) Unhedged Exposure

On Scenarios sheet:
	•	Build S_T from 0.95 × S0_in to 1.05 × S0_in
	•	Use 0.01 increments
	•	Compute:
USD_unhedged = FC_AMT * S_T

(B) Forward Hedge
	•	USD_forward = FC_AMT * F0_in
	•	Show constant across scenarios
	•	Include gray KPI summary

(C) Money Market Hedge (3-step)
	1.	Borrow EUR PV:
EUR_borrow = FC_AMT / (1 + R_FC * T_YRS)
	2.	Convert to USD at spot:
USD_invest_0 = EUR_borrow * S0_in
	3.	Invest USD:
USD_MM = USD_invest_0 * (1 + R_USD * T_YRS)

Show USD_MM across all scenarios and in gray KPI summary.

(D) Option Hedges

Use per-EUR premiums and 1:1 notional.

Put Hedge
	•	Premium_PUT_total = FC_AMT * PREM_PUT
	•	Payoff:
Payoff_PUT = MAX(K_PUT - S_T, 0) * FC_AMT
	•	Net proceeds (scenario-specific):
	•	If exercised: FC_AMT * K_PUT - Premium_PUT_total
	•	Else: FC_AMT * S_T - Premium_PUT_total

Call Hedge
Same structure, using K_CALL and PREM_CALL.
Include payoff profile and KPI.

(E) Sensitivity Table

Create a two-way data table or scenario table showing results over ±5% spot range.

(F) Charts

On Scenarios, produce a line chart with:
	•	Unhedged
	•	Forward
	•	Money Market
	•	Put
	•	Call

All plotted against S_T.

⸻

NAMED RANGE DEFINITIONS

Provide a complete “Audit_Map” sheet listing:
	•	Each named range
	•	Cell address
	•	Description
	•	All dependent formulas

Ensure traceability and auditability.

⸻

MODEL LOGIC (PSEUDOCODE)

Implement the following pseudocode explicitly in formulas:

S_T = sequence(0.95*S0_in , 1.05*S0_in , step=0.01)
USD_unhedged = FC_AMT * S_T

Forward:
  USD_forward = FC_AMT * F0_in

Money Market:
  EUR_borrow = FC_AMT / (1 + R_FC*T_YRS)
  USD_invest_0 = EUR_borrow * S0_in
  USD_MM = USD_invest_0 * (1 + R_USD*T_YRS)

Put Hedge:
  Premium_PUT_total = FC_AMT * PREM_PUT
  Payoff_PUT = max(K_PUT - S_T, 0) * FC_AMT
  USD_PUT_SCEN = if(S_T < K_PUT,
                     FC_AMT*K_PUT - Premium_PUT_total,
                     FC_AMT*S_T - Premium_PUT_total)

Call Hedge:
  Premium_CALL_total = FC_AMT * PREM_CALL
  Payoff_CALL = max(S_T - K_CALL, 0) * FC_AMT
  USD_CALL_SCEN = (FC_AMT*S_T + Payoff_CALL) - Premium_CALL_total


⸻

FORMATTING & COLOR CODING
	•	Inputs block (yellow) must be at the top of Inputs_Summary
	•	KPIs (gray) should appear in a dedicated output panel
	•	Formulas (green) must have consistent fill
	•	Clear section headers, bold / borders
	•	Use accounting number format for USD amounts
	•	Use 4 decimal places for FX rates

⸻

OUTPUT REQUIREMENTS

Produce:
	1.	A completed Excel workbook (.xlsx)
	2.	All calculations working
	3.	Fully dynamic updates when inputs change
	4.	Professional styling

⸻

VERIFICATION

Before producing the file, perform the following checks:
	1.	Interest parity check
Confirm:
F0_in ≈ S0_in * (1 + R_USD*T_YRS) / (1 + R_FC*T_YRS)
	2.	Forward vs Money Market equivalence
Verify USD_forward ≈ USD_MM.
	3.	Check all named ranges exist
Ensure Name Manager includes every required range.
	4.	Return full formula map
Provide a list of all formulas used in the workbook.

⸻

EXPORT

Return a downloadable .xlsx Excel file that satisfies all requirements.
