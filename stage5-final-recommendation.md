# Stage 5 – Final Analysis & Recommendation Memo  
## FX Hedging Strategy for EUR Receivable

---

## GOAL
Deliver an executive-ready summary of the FX hedging analysis for a EUR-denominated receivable, culminating in a clear, data-supported hedging recommendation. This memo emphasizes interpretation, strategic insight, and management-level decision making rather than mechanical computation.

---

## A. Exposure Summary

The firm is exposed to foreign exchange risk through a **EUR-denominated receivable of €4.5 million**, expected to be collected in **one year**. Because the firm reports financial results in USD, fluctuations in the EUR/USD exchange rate directly impact the dollar value of future cash inflows.

If the euro **depreciates** against the U.S. dollar, the USD value of the receivable declines, negatively affecting revenue, cash flow stability, and budget accuracy. If the euro **appreciates**, the firm benefits from higher USD proceeds. This asymmetric exposure introduces uncertainty into future cash flows and motivates the use of hedging strategies to manage FX risk.

---

## B. Summary of Hedge Outcomes

Four strategies were evaluated: **unhedged**, **forward hedge**, **money market hedge**, and **option-based hedges**.

The **forward hedge** locks in a fixed exchange rate, producing a known USD cash inflow regardless of future spot rates. This completely eliminates FX uncertainty but also removes any upside potential from favorable currency movements.

The **money market hedge**, implemented through borrowing EUR, converting at the spot rate, and investing USD, generates USD proceeds that are economically equivalent to the forward hedge. Minor differences arise only from rounding and interest conventions, confirming interest rate parity. Like the forward hedge, it provides certainty but requires balance sheet activity and liquidity management.

The **option hedge**, specifically a long EUR put, provides downside protection while preserving upside potential. If the euro depreciates below the strike price, losses are limited. If the euro appreciates, the firm benefits from higher spot rates, net of the option premium. The trade-off for this flexibility is the upfront premium cost, which reduces net proceeds in all scenarios.

The key insight is the **trade-off between certainty and flexibility**: forward and money market hedges eliminate risk entirely, while options convert FX risk into a known premium expense.

---

## C. Sensitivity Interpretation

When the euro **depreciates**, the unhedged position experiences a linear decline in USD proceeds. Both the forward and money market hedges remain constant, fully insulating the firm from adverse currency movements. The put option hedge establishes a floor on USD proceeds, limiting downside risk but reducing net outcomes due to the premium.

When the euro **appreciates**, the unhedged position benefits the most but exhibits high volatility. The forward and money market hedges forgo this upside entirely. The option hedge participates in favorable movements while still providing downside protection, though the premium creates a modest drag on performance.

In summary:
- **Forward / Money Market**: Maximum certainty, no flexibility, no premium  
- **Options**: Partial certainty, upside flexibility, premium cost  
- **Unhedged**: Maximum upside and downside volatility  

---

## D. Strategic Recommendation

**Recommended Strategy: Forward Hedge**

Given the one-year horizon and the firm’s exposure profile, the **forward hedge** is the most appropriate strategy.

This recommendation is supported by:
- Complete elimination of FX uncertainty
- Predictable USD cash flows
- No upfront premium cost
- Simplicity of execution and monitoring

While option hedges provide flexibility, the premium cost reduces expected proceeds and is better suited for firms with higher risk tolerance or speculative views on currency appreciation. In this case, management’s priority is stability rather than optionality.

---

## E. Executive Justification

From a management perspective, the forward hedge best aligns with core financial objectives:

- **Cash flow stability**: Ensures predictable USD inflows  
- **Budget certainty**: Simplifies forecasting and planning  
- **Liquidity efficiency**: No upfront premium or borrowing required  
- **Operational simplicity**: Straightforward execution and oversight  
- **Accounting clarity**: Easier hedge accounting treatment compared to options  

The money market hedge achieves similar economic results but introduces unnecessary balance sheet complexity, while option hedges introduce premium costs that are not justified given the firm’s risk profile.

---

## Extra Credit – Areas for Further Study & Improvement

### 1. Claude Skills (Automation & Live Data Integration)

Claude Skills could automate the FX hedging workflow by pulling **live FX spot rates and interest rates**, updating model inputs automatically, regenerating spreadsheets on demand, validating hedge parity conditions, and producing executive-level summary reports. This would significantly reduce manual updates and ensure models remain current.

---

### 2. OpenAI Codex / Code Interpreter

OpenAI Codex could convert the spreadsheet logic into **Python-based models**, validate formulas, and run advanced analyses such as **Monte Carlo simulations** or extended sensitivity loops. Codex also enables rapid regeneration of audit-ready models, reducing operational and model risk.

---

### 3. Claude Code / Multi-File Reasoning

Claude’s multi-file reasoning capabilities allow it to read and update **Excel, CSV, and Markdown files simultaneously**, ensuring consistency across versions. This enables automated model rebuilding, dashboard creation, and version-controlled documentation, enhancing transparency and scalability in the hedging process.

---
