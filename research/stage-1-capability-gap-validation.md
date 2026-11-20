# Stage 1 — Validate the LPL Capability Gap
## Desk-research memo — Inter IIT LPL Financials

**Date:** 20 November 2026  
**Status:** Desk research completed; internal capability validation still open  
**Related research:** [Portability-Adjusted Transition Optimizer](portability-adjusted-transition-optimizer.md) · [Transfer Rails & Regulatory Updates](transfer-rails-and-regulatory-updates.md)  
**Purpose:** Establish what LPL already publicly says it does, distinguish the different meanings of asset/client retention, identify what is still unknown, and define the minimum questions needed before proposing an add-on.

---

## 1. Executive conclusion

The broad transition problem is real, but the original framing needs to be sharpened.

LPL already publicly describes:
- A centralized transition/onboarding portal with task, timeline, progress, communication and status visibility.
- Dedicated Investment Transition, Regional Transition and Transition Support Partners.
- CAT (Client Account Tool) for advance collection/preparation of client and account information.
- IAT (Investor Account Tool) for orchestrating client data collection and repapering.
- Automation and validation intended to reduce incomplete submissions and rework.
- ClientWorks capabilities for digital account opening, householding, account conversion, money movement, reporting and trading.
- A separate Conversion Tool for brokerage-to-advisory account conversion.

Therefore, **do not build or pitch** another onboarding dashboard, task tracker, document collector, repapering workflow, NIGO checker, account-opening tool or generic transfer-status tracker.

A possible gap remains: **a pre-transition, household-level decision layer that compares the client-level financial consequences of different dispositions for each holding** (in-kind transfer, specialist route, broker-of-record change, liquidate, retain, defer, or manual review), and then evaluates the resulting household portfolio / financial plan.

But this is not yet a proven LPL gap. Public pages describe process capabilities, not the complete internal product stack or all specialist work performed by transition teams. We must ask LPL / the problem-statement owner directly.

**Stage 1 verdict: Continue discovery; no implementation authorization yet.**

---

## 2. Critical clarification: what does the “80%” mean?

### 2.1 A directly relevant LPL public number surfaced

In its Q3 2026 earnings prepared remarks (27 October 2026), LPL management said it expected approximately **83% final asset retention for the Commonwealth Financial Network conversion**, down from the 90% underwriting expectation. The Q3 investor presentation identifies Commonwealth as approximately 3,000 advisors and ~$340B of client assets as of 30 September 2026; the acquisition materials describe the 83% as an asset-retention assumption.

LPL's CFO attributed the change from around 85% signed advisors in the prior quarter to 83% to a small number of advisors who had signed but subsequently decided not to stay. This is important: at least part of the publicly discussed shortfall was **advisor-level attrition / a change of mind**, not necessarily NIGO, asset ineligibility or transfer friction.

Sources:
- LPL Q3 2026 prepared remarks: https://investor.lpl.com/static-files/4cd249c9-a4ec-400f-8d01-40c4a498a97f
- LPL Q3 2026 investor presentation: https://investor.lpl.com/static-files/e0ebb41e-5203-402e-9d39-2641a320637d
- InvestmentNews, 27 October 2026: https://www.investmentnews.com/independent-broker-dealers/lpl-financial-to-miss-90-target-on-commonwealth-asset-retention/268780
- AdvisorHub, 27 October 2026: https://www.advisorhub.com/lpls-trims-commonwealth-retention-forecast-to-83/

### 2.2 Do not conflate these metrics

| Metric | Publicly described figure | What it actually refers to | What it does not establish |
|---|---:|---|---|
| Commonwealth conversion asset retention | ~83% expected | Expected assets retained in the LPL conversion of Commonwealth | 17% of individual clients lost; 17% blocked by transfer paperwork |
| LPL overall asset retention | 97% in Q3 2026; 98% over trailing 12 months | LPL's company-wide asset retention metric | A new-advisor transition cohort or a client-level retention rate |
| LPL recruited advisor transition | 45 days average; 90% of AUM transitioned by second month | LPL's published transition progress / timeline claim | ACATS service-level time; 90% client retention; proof that residual assets are permanently lost |
| Informal “80% clients retained” statement | Unverified | Unknown until source and denominator are supplied | Cannot be used as a baseline, benchmark or model target |

The Commonwealth number is a plausible source of confusion behind the informal “80%” statement, but we cannot conclude it is the source without asking the person who supplied it.

### 2.3 Questions to resolve the denominator

1. Is the figure client count, account count, AUM, revenue, advisor headcount, or something else?
2. Is it about an individual advisor changing firms, a team move, a broker-dealer conversion, or an acquisition / bulk conversion such as Commonwealth?
3. Is the denominator all pre-move clients/assets, only clients who were eligible to move, or only clients who signed / consented?
4. At what date is retention measured: resignation, account opening, 30/60/90 days, month 2, or a later steady-state date?
5. Does “not retained” mean the client did not follow the advisor, the account did not open, the asset did not transfer, the client kept assets elsewhere by choice, or the asset was delayed?
6. Who supplied the figure and can they share the original source / slide / definition?

**Research rule:** Keep the 80% number out of product claims and quantitative assumptions until these questions are answered.

---

## 3. LPL's publicly disclosed capability map

This is a public-evidence map, not a claim to know LPL's internal architecture.

| Existing capability | What LPL publicly says it does | Product implication / boundary |
|---|---|---|
| Centralized onboarding portal | Consolidates communications, documentation, status updates, tasks, timelines and progress | Generic tracking / visibility is not a differentiator |
| Transition partners | Investment Transition Partner maps the current book and consults on investment products/platforms; Regional Transition Partner coordinates overall transition; Transition Support Partner assists with transfers and new account opening | Human expertise and coordination already exist; understand what analysis they perform manually |
| CAT | Collects/prepares client and account information in advance; intended to produce cleaner submissions | Do not recreate intake / data-preparation workflow |
| IAT | Orchestrates client data collection and repapering; reduces back-and-forth | Do not recreate e-sign / repapering / document chase |
| Automation and validation | Reduces manual touchpoints, incomplete submissions and rework | A generic NIGO detection feature likely overlaps |
| ClientWorks | New account opening, householding, account conversion, money movement, reporting and trading | Any add-on must integrate with, not replace, core advisor workstation |
| ClientWorks account conversion | Public page says accounts can be converted while preserving account numbers and historical data | Clarify exactly which conversion types are covered; this may refer to account conversion within LPL, not cross-firm portability |
| Conversion Tool | Simplifies brokerage-to-advisory conversion and moves entire accounts with minimal paperwork | This is not evidence of a tool that optimizes an external advisor's book transfer |
| ClientWorks Proposal / Rebalancer | Investment proposals, trading and rebalancing across models/accounts/security types | Existing portfolio construction/rebalancing capabilities may overlap with some post-transition portfolio analysis |
| Client-facing transition page | Says virtually all holdings should be transferable in most cases, with minimal paperwork | Ask what exceptions make up the residual; do not assume the average household has a large non-portable asset problem |

Primary sources:
- Transition process: https://www.lpl.com/join-lpl/establishing-your-business/transitioning-your-practice.html
- CAT / IAT and portal: https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/how-lpl-financial-is-redefining-advisor-transition-experience.html
- New transition guide (21 April 2026): https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/transition-your-financial-practice-with-confidence.html
- ClientWorks: https://www.lpl.com/join-lpl/managing-your-business/tech-capabilities-and-offerings/clientworks.html
- Advisory platforms / Conversion Tool: https://www.lpl.com/join-lpl/managing-your-business/products-platforms/advisory-platform-and-tools.html
- Investor-facing FAQ: https://www.lpl.com/investors/investors-new-to-lpl.html

### Important wording distinction

LPL's investor-facing FAQ says “virtually all” holdings should transfer in most cases. That is broad marketing language, not a position-level eligibility guarantee. It should prompt questions about exceptions and edge cases, not be read as proof that complex assets are never a problem.

---

## 4. Capability gap matrix

| Problem / proposed function | Public LPL capability evidence | Preliminary status | What we must verify |
|---|---|---|---|
| Advisor transition task tracking | Portal, task/timeline/progress visibility | Existing / likely duplicate | Are there any material blind spots? |
| Client data collection and account preparation | CAT | Existing / likely duplicate | Does CAT ingest holdings, cost basis and contract metadata or just account/client details? |
| Client repapering and e-sign | IAT, automation, eSignature | Existing / likely duplicate | What exceptions still require manual handling? |
| NIGO / submission validation | Automation and validation | Existing / likely duplicate | Does it identify only form defects or also asset-level eligibility / route constraints? |
| Transfer execution / status | Transition Support Partners, ClientWorks money movement and transfer workflows | Existing in some form; scope unclear | Which rails and asset types are actually supported end-to-end? |
| Asset-level portability classification | Investment Transition Partner maps current book; public CAT/IAT description does not specify position-level eligibility | Unknown | Is there a pre-move holdings-level portability report? |
| Specialist route selection (ACATS, Fund/SERV, I&RS, AIP, OCC, bilateral) | DTCC infrastructure exists; LPL public materials do not disclose its internal route decisioning detail | Unknown | Does LPL classify each asset by rail, eligibility, firm support and required approvals? |
| Compare in-kind vs liquidation vs retain vs defer | No explicit public description found | Potential gap; unverified | Do transition specialists model these alternatives today? |
| Tax-lot / realized gain impact of transfer disposition | Not explicitly described in transition materials | Potential gap; unverified | Is tax-lot data available and is route-level tax impact calculated? |
| Annuity guarantee / rider / surrender economics | Public materials do not describe this as part of advisor transition workflow | Potential gap; unverified | Are broker-of-record changes separated from contract exchanges / surrenders? |
| Household allocation / concentration after partial transfer | ClientWorks reporting/rebalancing exists; no public evidence of transition-specific mixed-asset scenario analysis | Unknown | Can LPL model held-away assets alongside assets that move? |
| Retirement / withdrawal-plan impact | LPL has broader financial-planning offerings; transition-specific linkage not publicly described | Unknown | Is the transition decision connected to the client's financial plan and withdrawal strategy? |
| Historical exception analytics / predictive delay risk | No specific public evidence found | Unknown | Are historical transfer outcomes, reason codes and durations analyzed? |

**Interpretation:** “Not publicly described” is not the same as “does not exist.” The matrix is a diligence agenda, not a competitive claim.

---

## 5. The product boundary we should defend

### Do not build

- Another onboarding / task management portal.
- Another document collection or e-signature flow.
- A generic NIGO checker.
- A replacement ACATS or transfer execution rail.
- A basic “transferable / non-transferable” lookup table.
- A tool that simply maximizes AUM moved or advisor revenue.
- A model that treats every asset remaining at the old firm as lost.

### Potentially differentiated analytical layer

For each household, compare feasible asset dispositions and quantify client consequences:

1. **Move in-kind** through the supported route.
2. **Use a specialist / alternate rail** where appropriate.
3. **Change broker / distributor of record** without changing the underlying insurance contract, where applicable.
4. **Liquidate and transfer cash**, with tax, fee and market-exposure consequences.
5. **Retain at the old institution** where that is the better client outcome.
6. **Defer** until maturity, lock-up expiry, issuer/carrier approval or other condition.
7. **Manual review** where data or eligibility is uncertain.

Then reconstruct the post-transition household: allocation, concentration, liquidity, fees, tax position, guarantees, held-away assets and impact on the existing financial plan.

This would be an extension of the financial engine—not an attempt to replace LPL's operating infrastructure.

---

## 6. The most important internal questions

### A. Understand the metric and pain
1. What exactly is the “80%” number? Can we see the source?
2. Is it client retention, AUM retention, account opening, or transfer completion?
3. What transition cohort does it describe?
4. What are the start/end dates and measurement horizon?
5. Is the residual 20% permanently lost, delayed, held away, or deliberately not moved?

### B. Decompose the loss / delay
6. Of the assets not moved by the target date, what share is due to advisor attrition, client refusal, incomplete paperwork/NIGO, account-registration mismatch, asset ineligibility, receiving-firm product restrictions, issuer/carrier processing, or deliberate retention?
7. Which asset types create the highest dollar-value exceptions?
8. Which exceptions cause the longest delays?
9. Are the problems concentrated in a few large households or spread across many small accounts?
10. Does the issue affect client count, account count, AUM, revenue, or advisor productivity most?

### C. Map what LPL already does
11. Does CAT capture position-level holdings, tax lots, cost basis, product identifiers, annuity contract data and restrictions—or primarily client/account details?
12. Does IAT handle only repapering / client data collection, or does it also recommend asset disposition?
13. Does the Investment Transition Partner produce an asset-by-asset portability / disposition plan?
14. Which rails are supported end-to-end by LPL's process: ACATS, Fund/SERV, I&RS / ACATS-IPS, AIP, OCC, and bilateral issuer/carrier routes?
15. Are transfer exceptions and their resolution reasons stored in a structured dataset?
16. Does ClientWorks represent retained / held-away assets and residual positions at household level?

### D. Test the proposed gap
17. Before a transition, can an advisor compare in-kind transfer, liquidation, retain and defer for each position?
18. Are realized capital gains, redemption/transfer fees, surrender penalties, guarantees/riders and time-out-of-market effects quantified?
19. Does LPL compare the post-transition household portfolio and financial plan under each route?
20. Can the system explain why retaining an asset is preferable when it is in the client's interest?
21. Which of these decisions are currently made manually by transition specialists or advisors?
22. Would an advisor use the analysis before client outreach, after account intake, or only when an exception occurs?

### E. Data feasibility
23. Can LPL provide anonymized historical position-level holdings and final disposition?
24. Can it provide route, delivering/receiving firm, exception code, dates, costs and final status?
25. Are tax lots / product restrictions / contract details available at the time the decision must be made?
26. What can be represented with synthetic data and public eligibility rules if internal data is unavailable?

---

## 7. Evidence to request (highest value first)

| Evidence | Why it matters | Minimum useful fields |
|---|---|---|
| Definition / source of 80% | Determines whether the problem is real and correctly framed | Metric, numerator, denominator, cohort, measurement date |
| Transition funnel for a representative cohort | Separates advisor/client attrition from operational transfer friction | Starting clients/accounts/AUM; signed; opened; submitted; accepted; transferred; residual |
| Residual asset breakdown | Identifies whether a portability optimizer is relevant | Asset type, value, reason not moved, final disposition |
| Exception / NIGO reason codes | Shows whether pain is operational or financial | Exception code, asset/account, timestamps, resolution |
| CAT / IAT workflow screenshots or demo | Prevents duplicating existing features | Inputs, outputs, validations, handoffs |
| Transition specialist sample output | Reveals what human experts already do | Asset-by-asset recommendation, reasons, alternatives, costs |
| Historical time/cost data | Enables a measurable baseline | Start/end dates, staff effort, route, direct cost |
| Anonymized household portfolio sample | Tests financial-engine fit | Account registration, holdings, cost basis, product metadata, values |

Do not request identifiable customer data. Use synthetic or properly anonymized/tokenized examples and follow LPL's data handling requirements.

---

## 8. Suggested 20-minute validation interview

**Opening (2 min):** “We are not proposing another onboarding portal or transfer tracker. We are trying to understand whether advisors have a decision-support problem when deciding what to do with each client's holdings during a move.”

**Metric (4 min):** Ask for the source and denominator of the 80% figure; reconcile it with the LPL public 83% Commonwealth asset-retention forecast and the separate 45-day / 90%-of-AUM-by-month-two transition statement.

**Workflow (5 min):** Walk through one anonymized household from initial holdings to final disposition. Ask where CAT, IAT, portal, transition specialists and ClientWorks enter the process.

**Decision gap (6 min):** Ask whether anyone compares transfer in-kind vs alternate route vs liquidation vs retain vs defer, including tax, fees, guarantees, allocation and plan impact. Ask for a real example where the decision changed because of economics rather than paperwork.

**Data / value (3 min):** Ask what historical data exists and what outcome the tool should improve: client benefit, AUM continuity, reduced tax/fees, lower advisor time, fewer unresolved assets or shorter transition time.

---

## 9. Go / no-go criteria for this add-on

### Go to Stage 2 (workflow and data validation) only if:
- The problem owner confirms a measurable transition pain point and its denominator.
- A material share of the pain is asset-level decision friction, not simply advisor/client choice or routine paperwork.
- LPL's current tools do not already provide the same route-by-route household financial analysis.
- Advisors / transition specialists can identify real decisions they currently make manually or without adequate quantitative support.
- Necessary inputs can be obtained or reasonably approximated.

### Re-scope or stop if:
- The “80%” figure is a client-retention claim caused mainly by advisor/client choice, with little asset-level decision friction.
- CAT/IAT or transition specialists already provide the proposed economic scenario analysis.
- The main issue is client persuasion, legal constraints or incumbent-firm conduct rather than a financial decision problem.
- No reliable data exists to classify routes or estimate consequences.
- The add-on only duplicates a status tracker, NIGO tool or transfer workflow.

### Current status

| Question | Current answer | Confidence |
|---|---|---|
| Does LPL have extensive transition workflow infrastructure? | Yes, publicly documented | High |
| Does LPL have dedicated investment / transition support roles? | Yes, publicly documented | High |
| Is there a public 83% Commonwealth asset-retention forecast? | Yes, announced in Q3 2026 | High |
| Does 83% mean only 83% of clients followed individual advisors? | No; public materials describe asset retention, not client count | High |
| Was the drop to 83% caused by NIGO / non-transferable holdings? | Not established; CFO publicly cited a small number of signed advisors deciding not to stay | Medium-high |
| Is the informal “80% clients retained” claim valid? | Unknown; denominator/source missing | Low |
| Does LPL have position-level route classification? | Public materials do not settle this | Unknown |
| Does LPL have household-level route economics optimization? | Public materials do not settle this | Unknown |
| Is the proposed add-on a confirmed gap? | No; remains a testable hypothesis | Low |

---

## 10. Sources and evidence notes

1. **LPL Financial Q3 2026 Earnings Prepared Remarks** (27 October 2026)  
   https://investor.lpl.com/static-files/4cd249c9-a4ec-400f-8d01-40c4a498a97f  
   Primary source for: 97% Q3 / 98% trailing-12-month overall LPL asset retention; expected 83% Commonwealth final asset retention; CFO explanation that a small number of signed advisors decided not to stay.

2. **LPL Financial Q3 2026 Investor Presentation**  
   https://investor.lpl.com/static-files/e0ebb41e-5203-402e-9d39-2641a320637d  
   Primary source for: Commonwealth scale, approximately 3,000 advisors and ~$340B of client assets as of 30 September 2026; 83% retention assumption used in financial estimates.

3. **LPL Financial — Financial Advisor Practice Transition**  
   https://www.lpl.com/join-lpl/establishing-your-business/transitioning-your-practice.html  
   Primary source for: 45-day average transition, 90% AUM by second month, transition partner roles, advisor portal, eSignature and client-retention messaging.

4. **LPL Financial — How LPL Financial Is Redefining the Advisor Transition Experience** (16 April 2026)  
   https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/how-lpl-financial-is-redefining-advisor-transition-experience.html  
   Primary source for: centralized onboarding portal, CAT, IAT, automation, validation, role-based activities and transition professionals.

5. **LPL Financial — Transition Your Financial Practice with Confidence** (21 April 2026)  
   https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/transition-your-financial-practice-with-confidence.html  
   Primary source for: CAT and IAT descriptions, account preparation and repapering sequence, advisor transition questions and account-movement process.

6. **LPL Financial — ClientWorks Integrated Advisor Workstation**  
   https://www.lpl.com/join-lpl/managing-your-business/tech-capabilities-and-offerings/clientworks.html  
   Primary source for: digital account opening, householding, account conversion, money movement, reporting and trading.

7. **LPL Financial — Wealth Management Platform Solutions**  
   https://www.lpl.com/join-lpl/managing-your-business/products-platforms/advisory-platform-and-tools.html  
   Primary source for: ClientWorks Proposal, Rebalancer and Conversion Tool (brokerage-to-advisory conversion).

8. **LPL Financial — What to Know When Your Advisor Moves to LPL Financial**  
   https://www.lpl.com/investors/investors-new-to-lpl.html  
   Primary source for investor-facing statements that most accounts should be easily transferable and virtually all holdings should transfer in most cases. Marketing language; not a guarantee.

9. **InvestmentNews — LPL Financial to miss 90% target on Commonwealth asset retention** (27 October 2026)  
   https://www.investmentnews.com/independent-broker-dealers/lpl-financial-to-miss-90-target-on-commonwealth-asset-retention/268780  
   Secondary reporting on the 83% forecast and CFO's explanation regarding signed advisors who changed their mind.

10. **AdvisorHub — LPL Trims Commonwealth Retention Forecast to 83%** (27 October 2026)  
    https://www.advisorhub.com/lpls-trims-commonwealth-retention-forecast-to-83/  
    Secondary reporting on the same forecast and context.

### Source-quality caveats
- LPL's own public pages are primary evidence for what LPL says its tools do, but they are marketing materials and do not reveal every internal feature or specialist workflow.
- Earnings remarks are primary evidence for management's reported metrics and explanations; the 83% number was a forecast before conversion, not necessarily the final realized result.
- Industry media is useful for context but does not replace LPL's underlying cohort data.
- Absence of a feature from public marketing materials is not evidence that the feature does not exist internally.

---

## 11. Change log

- **2026-11-20:** Stage 1 desk research completed. Mapped publicly described LPL transition infrastructure and differentiated it from the potential household-level financial decision layer. Identified LPL's 83% expected Commonwealth asset-retention forecast and the CFO's explanation that some signed advisors changed their mind; separated it from 97% / 98% company-wide asset retention and 45-day / 90%-AUM transition statistics. Added a capability-gap matrix, internal interview questions, evidence request list and go/no-go criteria. Internal validation remains open.
