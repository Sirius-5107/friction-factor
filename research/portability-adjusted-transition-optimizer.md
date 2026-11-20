# Portability-Adjusted Transition Optimizer
## Research dossier — Inter IIT LPL Financials

**Status:** Discovery / hypothesis validation  
**Last updated:** 20 November 2026  
**Repository:** https://github.com/Sirius-5107/friction-factor

---

## 0. Executive summary

### Research question
Can we add a decision-support layer to the existing financial-planning / transition engine that quantifies the household-level financial consequences of moving client assets when some holdings are difficult, costly, delayed or impossible to transfer in-kind?

### Preliminary conclusion
**Potentially yes — but this should be an analytical layer, not another transfer workflow.**

LPL already publicly describes substantial transition infrastructure: an advisor onboarding portal, transition specialists, CAT (Client Account Tool), IAT (Investor Account Tool), repapering automation and validation. LPL says its average advisor transition in 2026 took 45 days and that 90% of AUM had transitioned by the second month. A generic checklist, document tracker, NIGO detector or onboarding dashboard would therefore likely duplicate existing capabilities.

A more defensible product hypothesis:

> Before and during a transition, model each household's holdings at the asset level, identify realistic transfer paths and constraints, and compare the financial consequences of alternative treatments — transfer in-kind, change broker of record, liquidate and transfer cash, retain at the old institution, or defer action.

The output should quantify what is movable, what is delayed or stranded, what each route costs, and how each route changes the household's portfolio and financial plan. It must be willing to recommend retaining an asset where that is in the client's interest.

### Critical correction to the initial problem framing
The team heard an informal claim that "only 80% of clients are retained." This is **unverified** and must not be repeated as an industry or LPL statistic.

LPL's current public transition page instead states:
- Average transition in 2026: **45 days**.
- **90% of AUM transitioned by the second month**.

These are LPL-published figures, not independent industry benchmarks. They do not mean 10% of clients are lost, nor that 10% of assets are permanently lost. They also do not establish that each account transfer takes 45 days. The 45 days refers to the overall advisor transition.

---

## 1. Problem framing

### 1.1 Three different outcomes — do not conflate them

| Measure | Definition | Why it matters |
|---|---|---|
| Client retention | Share of clients who choose to continue with the advisor at the new firm | Relationship / practice continuity |
| AUM retention | Share of pre-transition assets that ultimately become assets under the advisor's new-firm relationship | Economic continuity |
| Transfer completion | Share of initiated accounts / positions successfully moved or otherwise resolved | Operational execution |

A practice could retain most clients but transfer a smaller share of AUM. Conversely, most AUM could move while a small number of client relationships are lost. AUM not transferred by a particular date may be delayed, held away, deliberately retained, or permanently lost; these are different outcomes.

**Required validation:** Ask the problem-statement owner exactly what the 80% figure measures, its denominator, cohort, time horizon, source and whether it means client count or AUM.

### 1.2 Two layers of transition friction

**Layer A — relationship and onboarding friction**
- Client does not consent to move or chooses to stay.
- Client is uncertain about the new firm, service model, fees or investment options.
- Client paperwork is incomplete or delayed.
- Account ownership / registration details do not match.
- Delivering or receiving firm raises a valid exception.
- Client communication and account-opening sequence create friction.

This layer is partly behavioral, legal, compliance and operational. A financial optimizer cannot solve all of it.

**Layer B — asset portability and financial friction**
- Some assets are not eligible for standard ACATS transfer.
- Some assets can move only through a separate non-ACATS process.
- Some holdings may move only after review, issuer consent or additional documentation.
- A receiving firm may not support a particular product or security.
- Selling an asset to make it portable may create tax, fee, market-exposure or investment consequences.
- Keeping an asset at the old institution can create fragmented oversight, ongoing fees or servicing complexity.
- Some insurance products require a broker-of-record change rather than an insurance-contract transfer.

Layer B is the stronger fit with the project's existing financial engine.

---

## 2. What the public evidence says

### 2.1 LPL's existing capabilities — competitive boundary

LPL's public materials describe:

1. **Centralized advisor onboarding portal** — visibility into activities, timelines, progress, communications and repapering.
2. **Transition specialists / onboarding partners** — tailored plans, investment-product and platform mapping, transfer support and new-account-opening support.
3. **CAT (Client Account Tool)** — streamlines client and account data collection and prepares information in advance.
4. **IAT (Investor Account Tool)** — orchestrates client data collection / repapering and reduces back-and-forth.
5. **Automation and validation** — cleaner submissions and fewer manual touchpoints.
6. **ClientWorks** — public materials describe new account opening, account conversion while preserving account numbers and historical data, money movement, reporting and trading.

Sources:
- LPL transition page: https://www.lpl.com/join-lpl/establishing-your-business/transitioning-your-practice.html
- LPL transition experience (updated 16 April 2026): https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/how-lpl-financial-is-redefining-advisor-transition-experience.html
- LPL ClientWorks: https://www.lpl.com/join-lpl/managing-your-business/tech-capabilities-and-offerings/clientworks.html

**Implication:** Do not pitch a generic portal, task tracker, onboarding checklist, repapering workflow, document collection tool or status dashboard as the differentiating add-on. The public materials do not establish whether LPL already has a household-level optimizer that compares the financial consequences of alternative treatments for difficult-to-transfer holdings. That is the gap to validate — not assume.

### 2.2 LPL transition statistics

LPL's transition page states that:
- Its team reduced advisor workload during transition by about 50% over the prior two years, with an 80% workload-reduction goal.
- Average transition in 2026 took 45 days.
- 90% of AUM transitioned by the second month.
- Client retention is described qualitatively as typically high; no public numeric client-retention percentage is supplied on that page.

Source: https://www.lpl.com/join-lpl/establishing-your-business/transitioning-your-practice.html

**Interpretation limits:**
- 45 days = average advisor transition, not necessarily the time for one ACATS transfer.
- 90% of AUM by month two = a timing / transition-progress statement, not a 90% client-retention rate.
- The residual 10% cannot automatically be called lost or non-transferable AUM.
- These are LPL's own published figures; methodology, cohort and calculation details are not disclosed on the page.

### 2.3 ACATS and transfer exceptions

The SEC's Investor Bulletin explains that most brokerage account transfers use ACATS. The receiving firm initiates the process using a Transfer Instruction Form (TIF); the delivering firm validates the request and provides asset information. Incorrect or incomplete instructions and unresolved exceptions can delay or restart a request.

The SEC lists examples of assets that may not transfer through a standard brokerage transfer:
- Securities proprietary to the old firm.
- Mutual funds / money-market funds not supported by the receiving firm.
- Private-placement limited partnership interests.
- Fractional shares.
- Bankrupt securities.

The investor may need to decide whether to sell and transfer cash, leave the asset at the old firm, or use another permitted route. Selling can have tax consequences and leaving assets behind may involve fees. Some non-ACATS processes may take up to 30 days.

Sources:
- SEC / Investor.gov, Investor Bulletin: https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-bulletins-79
- SEC, Tips on Avoiding Delays: https://www.sec.gov/about/reports-publications/investorpubsacctxferhtm

**Important annuity nuance:** The SEC bulletin explains that an annuity shown on a brokerage statement may be held by the insurance company. In such cases, the brokerage transition may involve changing the broker of record through ACATS. This is different from transferring the annuity contract to another insurer, which typically involves a sale of the annuity. Do not automatically model every annuity as a non-transferable asset or assume that a broker-of-record change incurs a surrender charge.

### 2.4 Why 45 days is not an ACATS service-level timeline

SEC / Investor.gov guidance describes standard transfers involving participating banks as typically occurring in approximately 3–5 business days after the old firm receives a correct TIF. The same guidance says non-ACATS transfers may take up to 30 days. Other SEC material notes that overall timing varies with assets, account type and institutions.

Sources:
- https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-bulletins-79
- https://www.sec.gov/about/reports-publications/investorpubsacctxferhtm

Therefore, a 45-day advisor transition likely includes a broader sequence: practice onboarding, account opening, client authorization, paperwork, account / asset transfers, exceptions and residual assets. This is a hypothesis about timeline components, not a verified decomposition. Obtain LPL's internal definition before quantifying time savings.

---

## 3. Asset portability taxonomy

The system should classify each **position / contract**, not only the account.

| Asset / situation | Possible route | Key checks | Potential financial impact |
|---|---|---|---|
| Listed stocks / ETFs / eligible bonds | ACATS in-kind, subject to firm and security eligibility | CUSIP, quantity, registration, restrictions, receiving-firm support | Usually avoids liquidation; market exposure may continue |
| Mutual fund supported by receiving firm | ACATS or applicable fund-transfer rail | Share class, fund availability, account type, transfer eligibility | Fees / share-class differences; avoid unnecessary sale |
| Proprietary or unsupported mutual fund | Liquidate, retain, or other permitted route | Fund availability, redemption restrictions, tax lot, fees | Realized gains/losses, fees, time out of market |
| Fractional shares | Residual cash / liquidation treatment may apply; firm-specific | Fractional-share policy, whole-share quantity | Small cash residual, possible realization |
| Private placement / LP / held-away asset | Direct issuer / custodian process, retain, or other route | Partnership agreement, transfer consent, eligibility constraints, issuer and custodian | Delay, legal / admin costs, illiquidity |
| Annuity contract | Broker-of-record change, servicing change, or separate contract exchange depending on objective | Carrier, contract type, rider/benefit, broker-of-record rules, surrender schedule | Possible loss of guarantees or surrender cost only if contract is surrendered/exchanged |
| Retirement account | Like-to-like trustee / custodian transfer where eligible | Account type, registration, plan rules, tax treatment | Tax risk if incorrectly distributed / re-contributed |
| Bank deposit / CD / cash product | Bank transfer, ACATS-for-banks if applicable, maturity / withdrawal route | Participating institution, maturity, early withdrawal penalty | Delay, penalty, interest / liquidity effect |
| Margin / pledged assets | Firm-specific transfer / payoff / re-documentation | Debit balance, collateral eligibility, lending terms | Financing cost, collateral disruption, forced-sale risk |
| Residual dividends / interest / cash | Residual sweep / follow-up transfer | Timing, account closure, residual policy | Small stranded balances and reconciliation workload |

This is a starting taxonomy, not a definitive eligibility rules engine. Actual eligibility depends on the asset, delivering firm, receiving firm, account registration, custody arrangements, product agreements and current policies. Each classification should carry a confidence level and evidence / source.

### 3.1 Annuity-specific caution

Separate these cases:
1. **Broker-of-record change:** Advisor servicing relationship changes while the contract remains with the same insurance carrier. This may not be a surrender or 1035 exchange.
2. **Contract exchange / replacement:** The client moves value to a different annuity contract or carrier. This may trigger surrender charges, new surrender periods, tax and benefit consequences, and replacement suitability requirements.
3. **Surrender / cash-out:** The contract is terminated for cash; consequences depend on contract terms and tax facts.

The optimizer should never recommend surrender or exchange based solely on portability. It should compare guarantees, riders, costs, tax status, surrender schedule, age and client objectives, with human review.

---

## 4. Product hypothesis

### Working name
**Portability-Adjusted Transition Optimizer**

### Product promise
"Understand the financial consequences of moving each client's assets before choosing how to transition them."

### Target user
- Advisor / transition team preparing a book of business for a move.
- Financial planner evaluating a specific household's holdings.
- Transition specialist identifying cases needing investment / tax / product review.

### Core workflow

1. **Ingest household holdings**
   - Accounts, registration, positions, quantities, market values, tax lots / cost basis, unrealized gains and losses.
   - Product / contract metadata and restrictions where available.
   - Source and as-of date for each field.

2. **Classify portability**
   - Likely in-kind / ACATS eligible.
   - Conditional / requires receiving-firm review.
   - Non-ACATS / issuer or carrier process.
   - Broker-of-record / servicing change.
   - Likely non-transferable / unsupported.
   - Unknown — manual review required.

3. **Generate feasible transition routes**
   - Transfer in-kind.
   - Transfer through alternate rail.
   - Liquidate and transfer cash.
   - Retain at old institution / held-away.
   - Defer until maturity / lock-up / other condition.
   - Change broker of record where appropriate.

4. **Calculate route-specific costs and consequences**
   - Realized capital gains / losses (tax estimate, not tax advice).
   - Transaction, redemption, transfer, custody and ongoing account fees.
   - Surrender charges / contract penalties where applicable.
   - Lost guarantees / rider value or other contract benefits.
   - Estimated time / process uncertainty.
   - Time out of market only if liquidation and reinvestment create an actual exposure gap.
   - Ongoing fragmentation / servicing costs if retained.

5. **Reconstruct the household portfolio under each route**
   - Asset allocation and concentration after transition.
   - Liquidity, income and risk exposures.
   - Tax location / account type where relevant.
   - Retirement / withdrawal plan impact, if connected to the existing planning engine.

6. **Compare scenarios and explain trade-offs**
   - Lowest immediate cost.
   - Lowest estimated tax realization.
   - Highest continuity of investment exposure.
   - Highest portability / consolidation.
   - Best fit with stated client objectives and constraints.
   - "Do not move / retain" as a legitimate outcome.

7. **Produce an advisor-ready review**
   - Asset-by-asset route and reason.
   - Assumptions, missing data and confidence.
   - Exceptions requiring human / compliance / tax / legal review.
   - Client-facing explanation only after advisor approval.

### Explicit non-goals
- Initiating ACATS requests or replacing custodian transfer rails.
- Replacing LPL CAT, IAT, onboarding portal or ClientWorks.
- Predicting which clients will defect without validated historical data.
- Automatically persuading clients to move assets.
- Giving legal, tax or insurance replacement advice.
- Treating all assets that remain behind as lost AUM.
- Optimizing advisor revenue at the expense of client suitability.

---

## 5. Fit with the existing Inter IIT PS

The current project concept already includes the following modules (from team discussions; validate against the latest PS specification):

| Existing module / concept | Relationship to this add-on |
|---|---|
| Structured holdings and tax-lot intake | Input foundation |
| Transferability rails: ACATS in-kind, Ex-Clearing / BOR / AIP, non-transferable assets, SBLOC | Portability classification and route generation |
| Transition economics: taxes, capital gains, surrender charges, fees and annuity break-even | Cost / consequence engine |
| Portfolio and retirement optimization | Reconstruct post-transition household portfolio and downstream plan |
| Client-facing proposal | Explain options and trade-offs |

**Potential gap:** The system may already classify transferability and calculate individual costs, but may not yet aggregate those effects into a household-level comparison of **partial transfer vs full transfer vs retain / defer** scenarios.

That aggregate decision layer is the proposed add-on. Before coding, inspect the current PS specification and determine whether this is genuinely new functionality or already implied by the existing engine.

### Product boundary test

If the output is merely:
- "This holding is non-transferable," or
- "This holding needs another form,"

then it is a transfer workflow / classification tool.

If the output is:
- "Here are three feasible ways to handle this household's assets; here are the estimated tax, fee, liquidity, guarantee, allocation and planning consequences of each; this is the trade-off and uncertainty,"

then it is financial decision support and more clearly connected to the PS.

---

## 6. Quantitative framework (proposed, not implemented)

### 6.1 Decision variables

For each asset position i, choose one feasible route r from the position's allowed route set:
- IN_KIND
- ALT_TRANSFER
- BROKER_OF_RECORD
- LIQUIDATE_CASH
- RETAIN_OLD_FIRM
- DEFER
- MANUAL_REVIEW

Only routes supported by product / institution rules should be considered feasible.

### 6.2 Route cost

For position i and route r, estimate:

**C(i,r) = Tax(i,r) + ExplicitFees(i,r) + Penalties(i,r) + ExpectedOngoingCost(i,r) + ExpectedMarketGapCost(i,r) + BenefitLoss(i,r)**

Do not double-count. Some terms may be non-monetary or not reliably quantifiable; present them separately rather than forcing false precision.

- **Tax:** estimated tax from realized gains / losses, conditioned on account type and tax assumptions.
- **ExplicitFees:** transfer, transaction, redemption, custody and account fees.
- **Penalties:** surrender charges, early withdrawal penalties or contract-specific charges.
- **ExpectedOngoingCost:** incremental costs of maintaining an old account / fragmented assets.
- **ExpectedMarketGapCost:** only when assets are liquidated and exposure is interrupted; model with scenario assumptions, not a deterministic forecast.
- **BenefitLoss:** value of forfeited guarantees, riders, insurance features or contractual rights; often requires specialist valuation and should be flagged if not estimable.

### 6.3 Household objective

A first-pass objective could minimize total estimated transition friction:

**minimize Σᵢ Σᵣ x(i,r) × C(i,r)**

subject to:
- Exactly one route per asset (unless split quantities are permitted).
- Account / registration constraints.
- Receiving-firm product eligibility.
- Contract / issuer / lock-up restrictions.
- Client liquidity and investment-policy constraints.
- Tax and regulatory constraints.
- Client-approved exclusions / preferences.

This simple objective is not sufficient on its own. Add explicit constraints or a multi-objective / Pareto comparison for:
- Portfolio allocation drift.
- Concentration and liquidity.
- Retirement income / withdrawal needs.
- Guarantee / insurance protection.
- Operational feasibility and timing.

Do not collapse client suitability, legal eligibility and all risk dimensions into one opaque "friction score."

### 6.4 Time and uncertainty

For each route, estimate a range or distribution for completion time only if historical observations or defensible assumptions exist. Distinguish:
- Firm-wide advisor transition duration.
- Account-opening / repapering duration.
- ACATS processing duration.
- Non-ACATS / issuer / carrier duration.
- Exception resolution duration.
- Residual sweep duration.

A scenario table (optimistic / base / delayed) is preferable to unsupported machine-learning prediction.

### 6.5 Outputs and metrics

**Household-level outputs**
- Total market value by route category.
- Share of AUM expected to move in-kind / alternate rail / broker-of-record / liquidate / remain / unresolved.
- Estimated one-time transition cost range.
- Estimated tax realization range.
- Assets requiring human review.
- Post-transition allocation and concentration.
- Unresolved / retained asset value and reason.
- Scenario comparison and recommendation rationale.

**Pilot metrics**
- AUM classified with high confidence.
- Share of holdings requiring manual review.
- Difference between estimated and realized transition costs.
- Time from intake to advisor-ready transition plan.
- Exception rate / NIGO rate (only if actual workflow data exists).
- Share of AUM moved by route and time bucket.
- Number / value of assets retained for a documented client-beneficial reason.
- Advisor review acceptance / override rate.
- Client outcome / suitability guardrails.

Avoid "increase client retention by X%" as a success target until there is baseline data and a causal path from this feature to that outcome.

---

## 7. Illustrative example (synthetic — not an LPL case)

A household has $700,000 in assets:
- $350,000 listed securities and eligible funds.
- $100,000 mutual funds whose receiving-firm availability must be checked.
- $150,000 annuity value.
- $100,000 private / alternative / other holdings.

The system should **not** assume that $350,000 is definitely transferable or that the remaining $350,000 is stuck. It should request security identifiers, fund availability, account registration, carrier / contract details, issuer restrictions and receiving-firm acceptance.

Possible outputs after validation:
- Listed holdings: transfer in-kind if eligible.
- Unsupported funds: compare sale vs retain vs alternate route, including tax lots and fees.
- Annuity: determine whether the task is only broker-of-record change or an actual contract exchange / surrender.
- Private holding: determine issuer / custodian transfer rules and whether retaining is the only practical route.

Then compare the household's resulting portfolio and financial plan under the feasible alternatives. All numbers in this example are illustrative only.

---

## 8. Risks, constraints and guardrails

1. **Suitability:** Lowest cost or highest portability is not necessarily best for the client.
2. **Tax uncertainty:** Tax outcomes depend on tax lots, account type, holding period, loss carryforwards, jurisdiction and individual facts. Outputs must be estimates with assumptions.
3. **Annuity complexity:** Broker-of-record change is not the same as contract exchange / surrender. Avoid blanket surrender-charge assumptions.
4. **Data quality:** Statements may have stale values, missing CUSIPs, incomplete cost basis, unclear product names or incomplete contract details.
5. **Firm-specific rules:** Transfer eligibility depends on both delivering and receiving firms and may change. Classifications need effective dates and confidence.
6. **Legal / compliance:** No automated advice to evade restrictions, solicit clients improperly, or induce unsuitable replacement transactions. Advisor / compliance approval is required.
7. **Privacy / data security:** Holdings and tax-lot information are highly sensitive financial data. Prototype with synthetic or appropriately de-identified data.
8. **False precision:** Do not estimate the value of guarantees, client-retention uplift or time savings without adequate data.
9. **Conflict of interest:** The product must permit "retain at old firm" and "do not transact" as valid outcomes.

---

## 9. What we still need to validate

### Priority questions for LPL / senior / problem-statement owner

**A. Define the observed problem**
1. What exactly is the reported 80%: client count, accounts, AUM, revenue or something else?
2. What is the source and cohort behind the 80% figure?
3. Is 45 days the end-to-end advisor transition duration? What are the start and end events?
4. What does "90% of AUM by the second month" mean operationally, and what happens to the remaining 10%?

**B. Understand difficult assets**
5. Which asset classes most often fail to move in-kind in real transitions?
6. How much AUM is typically in non-ACATS / held-away / proprietary / private-placement / annuity / bank products?
7. What share of assets is ultimately retained by client choice versus product restrictions versus unresolved paperwork?
8. Are annuity issues usually broker-of-record changes, actual exchanges, or both?
9. Which transfer problems are already solved by LPL's transition partners / existing tools?

**C. Identify the product gap**
10. Does LPL currently produce an asset-level portability report before an advisor transition?
11. Does it calculate household-level tax / fee / guarantee / allocation consequences for alternative routes?
12. Can it compare partial transfer, full transfer, retain and defer scenarios?
13. Does it show the impact of assets left at the prior institution on the client's financial plan?
14. Which of these outputs would an advisor actually use to make a decision?

**D. Obtain usable evidence**
15. Can we access anonymized historical holdings and transfer outcomes?
16. Can we obtain route-level costs, dates, exception codes and final disposition?
17. Can we get product eligibility rules / supported security lists with update dates?
18. Can we interview transition specialists, advisors and operations staff?

### Minimum evidence needed before building
- A confirmed, recurring pain point not already handled by CAT / IAT / onboarding portal.
- A representative asset-level dataset or credible synthetic dataset grounded in documented rules.
- A clear decision that advisors currently make manually or cannot make with existing tooling.
- At least one measurable client-benefit metric beyond "faster transfer."

---

## 10. Research plan and next actions

### Phase 1 — Confirm the problem
- [ ] Ask senior to define the 80% statistic and 45-day timeline.
- [ ] Ask which asset types drive the longest / most expensive exceptions.
- [ ] Separate client refusal, paperwork / NIGO, transfer rejection, non-ACATS, non-transferable assets and post-transfer residuals.

### Phase 2 — Map existing LPL capabilities
- [ ] Document CAT, IAT, portal, transition specialists and ClientWorks.
- [ ] Ask specifically whether LPL has a household-level economic scenario optimizer.
- [ ] Identify which calculations are already in the core PS and which are missing.

### Phase 3 — Evidence and model
- [ ] Build an asset portability taxonomy with source, effective date and confidence.
- [ ] Define a synthetic household dataset with representative account types / assets.
- [ ] Model route-level costs and downstream portfolio effects.
- [ ] Compare full transfer, partial transfer, retain and defer cases.
- [ ] Validate assumptions with a transition specialist / advisor.

### Phase 4 — Decide whether to build
- [ ] If existing LPL tools already do this, drop or materially change the add-on.
- [ ] If the gap is confirmed, define the narrow MVP and measurable success criteria.
- [ ] Keep execution / paperwork automation outside the MVP.

---

## 11. Current assessment

| Dimension | Preliminary assessment | Confidence |
|---|---|---|
| Real-world existence of non-transferable / difficult-to-transfer assets | Confirmed by SEC investor guidance | High |
| Potential financial consequences of liquidation / retaining assets | Confirmed in principle by SEC guidance | High |
| LPL already has substantial onboarding / repapering infrastructure | Confirmed by LPL public materials | High |
| LPL average transition is 45 days; 90% AUM by month two | LPL-published statement | High that LPL says it; independent validation unavailable |
| 80% client-retention statistic | Unverified | Low |
| LPL lacks household-level transition economics optimizer | Not established | Low |
| Proposed optimizer is a genuine unmet need | Plausible hypothesis, not validated | Low–medium |
| Fit with existing Inter IIT engine | Strong conceptual fit; confirm against latest PS spec | Medium–high |

### Go / no-go recommendation
**Proceed with research; do not start implementation yet.**

The best candidate is not a "transfer friction remover" in the generic operational sense. It is a **household-level portability and transition-economics decision layer** that makes difficult asset decisions explicit and quantifies their downstream financial consequences.

The feature is worth pursuing only if LPL confirms that this decision-support layer is not already available through its transition specialists and current technology.

---

## 12. Sources

1. **LPL Financial — Financial Advisor Practice Transition**  
   https://www.lpl.com/join-lpl/establishing-your-business/transitioning-your-practice.html  
   Used for: 45-day average transition, 90% AUM by second month, transition specialists, advisor portal, qualitative client-retention claims.

2. **LPL Financial — How LPL Financial Is Redefining Advisor Transition Experience** (updated 16 April 2026)  
   https://www.lpl.com/join-lpl/why-choose-lpl/news-and-insights/how-lpl-financial-is-redefining-advisor-transition-experience.html  
   Used for: onboarding portal, CAT, IAT, automation, validation, role-based activities and client-retention support.

3. **LPL Financial — ClientWorks Integrated Advisor Workstation**  
   https://www.lpl.com/join-lpl/managing-your-business/tech-capabilities-and-offerings/clientworks.html  
   Used for: new account opening, account conversion, money movement, reporting and trading capabilities.

4. **SEC / Investor.gov — Investor Bulletin: Transferring Your Investment Account** (27 June 2014)  
   https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-bulletins-79  
   Used for: ACATS process, asset eligibility examples, tax / fee implications of non-transferable assets, non-ACATS timing, annuity broker-of-record distinction.

5. **SEC — Transferring Your Brokerage Account: Tips on Avoiding Delays** (15 April 2009)  
   https://www.sec.gov/about/reports-publications/investorpubsacctxferhtm  
   Used for: common delay factors, account registration mismatches, forms and transfer process.

### Source-quality notes
- LPL sources are primary sources for what LPL publicly claims about its own tools and transition performance, but are marketing materials rather than independent evaluations.
- SEC / Investor.gov sources are authoritative investor education material, but some cited bulletins are older. Confirm current rules and firm-specific procedures before implementation.
- No external source reviewed so far proves the reported 80% client-retention figure or establishes that LPL lacks a household-level portability economics optimizer.
- All proposed product functionality and quantitative methods in this dossier are hypotheses / design proposals unless explicitly labelled as sourced facts.

---

## 13. Change log

- **2026-11-20:** Initial research dossier created. Reframed the reported "80% retention" claim as unverified; incorporated LPL's public 45-day / 90%-of-AUM-by-second-month figures; mapped LPL's existing CAT / IAT / portal / ClientWorks capabilities; documented SEC guidance on ACATS, non-transferable assets, non-ACATS timing and annuity broker-of-record distinctions; proposed a household-level portability-adjusted transition economics layer.
