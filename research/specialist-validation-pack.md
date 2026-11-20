# Specialist Validation Pack — Portability-Adjusted Transition Optimizer

**Project:** Inter IIT LPL Financials  
**Purpose:** Validate the proposed add-on's capability gap with transition specialists / Investment Transition Partners and obtain structured cases.  
**Scope guardrail:** This is research to validate one analytical decision-support add-on to the existing PS. It is not a proposal for onboarding, workflow tracking, transfer execution or a new platform.

## 1. Interview plan

**Participants:** 1–2 transition specialists / Investment Transition Partners.  
**Suggested duration:** 20–30 minutes.  
**Approach:** Ask for a walkthrough of actual practice first. Do not pitch the proposed solution until the current process is understood.

### Opening

"We are exploring a decision-support add-on to an existing financial-planning / transition engine. We are not trying to replace transfer operations or build another onboarding workflow. We want to understand how specialists decide what should happen to each asset in a mixed-asset household, and whether the financial consequences are already compared systematically."

### Core questions

1. **Current decision process:** "Walk me through how you currently decide the route and disposition for a mixed household that includes mutual funds, an annuity and a non-ACATS / alternative holding. What happens from the point you receive the holdings to the point the transition plan is agreed?"
2. **Existing analysis:** "What analysis do you already perform on tax impact, redemption / transfer fees, surrender risk, guarantee or rider preservation, liquidity and the household's post-transition allocation?"
3. **Manual work and missing data:** "What information do you wish you had earlier? Which decisions still depend on spreadsheets, email, specialist knowledge or repeated calls to product providers / firms?"
4. **Retain as an outcome:** "Do you ever explicitly recommend that an asset remain at the old institution because moving it would be worse for the client? How is that decision recorded and explained?"
5. **Existing tools:** "Is there an internal tool, report, spreadsheet or standard operating procedure that already shows position-level portability together with the financial consequences of each route?"
6. **Household-level view:** "After deciding what happens to individual positions, who checks the combined effect on allocation, concentration, liquidity and the client's financial plan? Is that analysis automatic, manual or not usually done?"
7. **Decision timing and usefulness:** "At what point would a comparison of alternative asset treatments be most useful—before client outreach, after holdings are collected, or when a specific exception appears?"
8. **Validation:** "Could you walk us through one anonymized case where the choice between transfer, alternate route, liquidation, retain or defer materially mattered? What did the specialist actually compare?"

### Follow-up probes (use only when relevant)

- Which asset classes or product types create the most difficult decisions?
- Are route rules different by delivering firm, receiving firm, account registration, share class, carrier or issuer?
- How do you represent uncertainty when eligibility or costs are not yet confirmed?
- What is the most common reason an initial recommendation changes?
- What would make you trust or reject an analytical recommendation?
- Which parts of this process are already solved well by existing LPL tools?

### Interview recording template

| Field | Notes |
|---|---|
| Role / experience (no personal identifiers needed) | |
| Current process and handoffs | |
| Existing tools / reports / spreadsheets | |
| Position-level portability analysis already performed? | |
| Tax / fee / surrender / guarantee analysis already performed? | |
| Household-level scenario comparison already performed? | |
| Retain / defer recommendation supported? | |
| Manual steps / tribal knowledge | |
| Missing or late-arriving data | |
| Most painful asset / decision types | |
| Potential gap confirmed? Evidence | |
| Proposed add-on value / likely adoption point | |
| Contradictory evidence / reasons not to build | |

**Interview discipline:** Distinguish what the participant personally does, what their team does, what an internal tool does and what they believe another team does. Record examples and artifacts where possible. Do not treat one person's workflow as an LPL-wide fact.

## 2. Structured case request

Ask for **two cases if feasible**:
- **Case A — interesting mixed-asset case:** a transition where multiple routes were genuinely considered or where an asset was retained, deferred, liquidated or handled through a specialist route.
- **Case B — typical case:** a more ordinary household / transition, to test whether the proposed feature solves a frequent enough decision problem rather than only unusual edge cases.

If only one case is available, prioritize Case A. Request an anonymized / synthetic reconstruction if sharing actual client information is not permitted. Do not request names, account numbers, addresses, tax IDs, exact dates that could identify a client, or raw statements.

### Case-level context

| Field | Requested value |
|---|---|
| Case ID (anonymous label) | |
| Case type | Interesting mixed-asset / Typical |
| Approximate household asset value band | |
| Number of accounts and broad account types | |
| Delivering / receiving firm types (can be generalized) | |
| Approximate transition period (month / quarter only) | |
| Client constraints relevant to disposition | |
| Was the case completed or still in progress? | |

### Position-level data template

One row per position or contract. Use ranges or synthetic values if exact values are sensitive.

| Field | Description / example |
|---|---|
| Position ID | Anonymous identifier |
| Asset / product category | Listed security, mutual fund, annuity, private investment, deposit, etc. |
| Identifier availability | CUSIP / ticker / product code available? Do not provide sensitive account identifiers |
| Approximate market value | Value or value band |
| Account registration / tax wrapper | Taxable, IRA / qualified, trust, etc. |
| Cost basis / unrealized gain-loss | Exact, approximate, unavailable, or not applicable |
| Product / contract restrictions | Lock-up, surrender schedule, issuer consent, proprietary status, etc. |
| Delivering-firm support known? | Yes / No / Unknown |
| Receiving-firm support known? | Yes / No / Unknown |
| Routes considered | In-kind, alternate rail, BOR, liquidate, retain, defer, manual review |
| Route actually selected | Selected disposition |
| Reason selected | Client interest, eligibility, cost, product restriction, preference, etc. |
| Alternatives rejected | Which routes and why |
| Tax consequence considered | Estimate / amount band / not assessed / not applicable |
| Fees / penalties considered | Estimate / amount band / not assessed / not applicable |
| Guarantees / benefits affected | Description or review flag |
| Liquidity / market exposure impact | Description or estimate |
| Expected vs actual timing | Broad range, if available |
| Manual review / escalation | What required specialist involvement? |
| Outcome / unresolved items | Final status, retained assets, follow-up still required |
| Confidence / source | Confirmed by firm / issuer / carrier, inferred, or unknown |

### Household-level case output

| Field | Requested value |
|---|---|
| Starting household assets (approximate) | |
| Value moved in-kind | |
| Value moved through alternate routes / BOR | |
| Value liquidated and transferred | |
| Value retained at old institution | |
| Value deferred / unresolved | |
| Total estimated tax / fees / penalties | |
| Post-transition allocation reviewed? | Yes / No; by whom / how |
| Financial-plan impact reviewed? | Yes / No; how |
| Was a household-level scenario comparison produced? | Yes / No |
| Existing artifact available? | Redacted report / spreadsheet / none |
| What decision was hardest? | |
| What analysis was missing or slow? | |

## 3. Case review scorecard

Use the case to answer these questions—not to build the full product around one unusual story.

| Test | Evidence to look for | Finding |
|---|---|---|
| Does the current process already create a position-level route plan? | Report / spreadsheet / documented process | |
| Does it compare alternative routes for the same position? | Side-by-side cost and consequence analysis | |
| Are tax, fees and penalties calculated systematically? | Inputs, assumptions, calculations, review owner | |
| Are annuity BOR changes distinguished from surrender / exchange? | Explicit contract treatment | |
| Are guarantees / riders and liquidity consequences considered? | Written review or specialist escalation | |
| Is the combined household portfolio reconstructed? | Before / after allocation, concentration, liquidity | |
| Is retain / defer treated as a legitimate client outcome? | Documented rationale | |
| What remains manual or invisible? | Specific repeated work / missing analysis | |
| Would the proposed analytical output change or accelerate a decision? | Participant feedback tied to this case | |

### Gap-confirmation decision

- **Gap confirmed:** Current process lacks a useful, repeatable household-level comparison of feasible asset routes and their consequences; specialist identifies a concrete decision improved by the proposed output.
- **Partial gap:** Some analysis exists, but is fragmented across tools / spreadsheets / specialists, or does not connect position-level choices to household-level effects. Narrow the feature to the missing integration.
- **No material gap:** Existing tools and specialist process already produce substantially the same position-level and household-level comparison. Do not build a duplicate.
- **Insufficient evidence:** Case or interview lacks enough detail. Request a second case or a demonstration of the existing artifact; do not infer a gap.

## 4. Parallel synthetic development fixture

Do not wait for a real case to test calculation correctness. Continue using the synthetic $1 million household in the design specification as the primary development fixture.

Build controlled variants from the same base case:
1. **Base:** listed securities, mutual funds, annuity and private investment.
2. **Tax-lot sensitivity:** same unsupported fund with low vs high embedded unrealized gain.
3. **Annuity route distinction:** broker-of-record change vs contract surrender / exchange, with contract facts explicitly supplied.
4. **Account-type variation:** taxable vs qualified account to test tax treatment.
5. **Eligibility uncertainty:** receiving-firm support unknown vs confirmed vs rejected.
6. **Retain / defer:** holding remains at old institution or waits for a defined event.
7. **Data-quality failure:** missing cost basis, stale valuation, missing identifier or contradictory rule record.

For each variant, create hand-worked expected outputs before implementing calculators. Keep assumptions explicit and label all synthetic values.

## 5. Ordered work plan

1. Conduct the structured capability interview with 1–2 specialists.
2. Request the structured Case A and Case B templates (in parallel with the interview).
3. Review the available cases against the scorecard and decide whether the capability gap is confirmed, partial, absent or still unknown.
4. In parallel, continue synthetic fixture design and hand-worked calculation tests.
5. Only after gap confirmation, refine the production-facing rules table, calculators and scenario-generation logic around the validated missing capability.

## 6. Scope protections

The interview and case request must not expand the product into:
- Onboarding portals, task tracking, document collection, e-signature or NIGO workflow.
- ACATS / alternate-rail execution or transfer-status tracking.
- Client-retention prediction or unsupported retention-uplift claims.
- Maximizing AUM moved or advisor revenue.
- A single opaque friction score that hides suitability, legal eligibility or client trade-offs.

The fixed product remains a household-level analytical decision-support add-on to the existing PS.
