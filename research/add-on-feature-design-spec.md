# Add-on Feature Design — Portability-Adjusted Transition Optimizer

**Project:** Inter IIT LPL Financials  
**Status:** Concept and solution-design brief for the development team  
**Date:** 20 November 2026

## 1. Purpose

Define one analytical add-on to the existing PS. The add-on helps an advisor decide how to handle a household's assets during an advisor transition by comparing feasible disposition routes and their financial consequences.

This is a concept and implementation blueprint, not a request to build a new transfer platform or replace the existing PS. The development team will own production implementation.

## 2. Fixed product definition

**Working name:** Portability-Adjusted Transition Optimizer.

**One-line description:** A household-level decision-support layer that compares feasible ways to transition each asset and shows the financial and portfolio consequences of the resulting combination.

The feature is not a transfer-execution tool. It does not initiate ACATS, open accounts, collect signatures, chase documents, or manage transition tasks.

## 3. User problem

A household may hold assets with different transfer characteristics. Some can move in-kind, some require a specialist or alternate transfer route, some may need a broker-of-record change, and others may be better retained or deferred.

Choosing a route asset by asset can create household-level consequences that are easy to miss: realized gains, fees, penalties, lost guarantees, liquidity changes, concentration, fragmented holdings, or a changed retirement plan.

The add-on makes those trade-offs visible before the advisor finalizes the transition approach.

## 4. Illustrative household (synthetic)

| Holding | Market value | Example issue |
|---|---:|---|
| Listed stocks and ETFs | $400,000 | In-kind transfer subject to security and firm eligibility |
| Mutual funds | $200,000 | Receiving-firm support may vary by fund/share class |
| Annuity | $250,000 | May require broker-of-record change rather than contract surrender |
| Private investment | $150,000 | Issuer consent, alternate processing or retention may be required |
| **Total** | **$1,000,000** | Synthetic example; not an LPL client or observed case |

The feature should not assume that all listed securities are eligible, all mutual funds are blocked, an annuity must be surrendered, or a private investment cannot move. It must evaluate the actual position, account, firms and contract details.

## 5. Functional workflow

### Step 1 — Consume existing PS data

Reuse the existing PS's structured household, account, holdings, tax-lot, portfolio and client-constraint inputs wherever available. Do not create a parallel intake workflow.

Required data includes:
- Household and account identifiers (pseudonymized in prototype data).
- Account registration and tax wrapper.
- Security / product identifier, quantity, market value and as-of date.
- Tax lots, cost basis and holding period where relevant.
- Delivering and receiving institution / platform.
- Product metadata, contract terms, restrictions and fees where relevant.
- Client liquidity needs, investment policy and other constraints.
- Data source, freshness and confidence for each material field.

### Step 2 — Determine portability and feasible routes

Classify each position using a non-binary status:
- Likely in-kind / standard transfer route.
- Conditional; receiving-firm or delivering-firm confirmation required.
- Alternate rail / issuer / carrier process.
- Broker-of-record or servicing change.
- Likely unsupported / not transferable to the destination.
- Unknown; manual review required.

For each position, generate only feasible candidate routes:
- Transfer in-kind.
- Transfer through an applicable alternate route.
- Change broker / distributor of record where appropriate.
- Liquidate and transfer cash.
- Retain at the old institution.
- Defer until a restriction, maturity or approval condition clears.
- Manual review.

Eligibility is firm-, account-, product- and date-dependent. Every classification should retain its source, effective date, confidence and reason. Unknown must remain unknown; do not infer eligibility from asset name alone.

### Step 3 — Calculate route consequences

For each feasible position-route pair, estimate and separately report:
- Realized gain / loss and estimated tax, using account type and available tax-lot information.
- Transaction, transfer, redemption, custody and account fees.
- Surrender charges or early-withdrawal penalties where actually applicable.
- Contractual benefits or guarantees potentially lost.
- Ongoing cost of retaining / servicing assets at the old institution.
- Time out of market only where liquidation creates an actual exposure gap.
- Liquidity and access implications.
- Expected timing range only where supported by observed data or explicit assumptions.

Do not double-count costs. Do not force unquantifiable guarantee value, suitability, legal risk or uncertainty into a made-up dollar estimate. Flag them for specialist review.

### Step 4 — Build household scenarios

Generate feasible combinations across positions. Example scenarios:
- Move eligible assets in-kind; retain the private investment.
- Move eligible assets; liquidate selected unsupported funds after tax-lot analysis.
- Move eligible assets; change the annuity broker of record; retain the private investment.
- Defer selected positions pending issuer / carrier approval or maturity.

These are examples, not hard-coded preferred outcomes. Scenario generation must respect the actual feasible-route set and client constraints.

### Step 5 — Reconstruct and compare the household

For each scenario, calculate:
- Amount and share of assets by route.
- One-time fees, estimated tax realization and penalty ranges.
- Assets retained, deferred or unresolved, with reasons.
- Post-transition asset allocation and concentration.
- Liquidity and income implications.
- Ongoing fragmentation / account cost where data exists.
- Impact on connected portfolio, retirement or withdrawal-planning outputs in the existing PS.

### Step 6 — Present advisor-ready decision support

The output should contain:
1. Position-level route, rationale, feasibility and confidence.
2. Scenario comparison with separate cost / tax / liquidity / portfolio dimensions.
3. Key assumptions and missing data.
4. Items requiring advisor, tax, legal, insurance or compliance review.
5. A clear explanation of why a route is recommended and what alternatives were rejected.

The system may recommend retaining an asset at the old institution where that better serves the client. It must not optimize simply for assets moved or advisor revenue.

## 6. Optimization formulation

Let (x_{ir}=1) when position (i) is assigned route (r), and 0 otherwise. A first-pass optimizer can minimize estimated monetary transition friction:

\[
\min \sum_i \sum_r x_{ir} C_{ir}
\]

where (C_{ir}) is the estimated route-specific monetary cost for position (i).

Subject to:
- Each position receives one permitted treatment (or a permitted split if the product supports partial quantities).
- Infeasible routes are excluded.
- Account registration, contract, issuer and firm restrictions are respected.
- Client liquidity and investment-policy constraints are maintained.
- Portfolio constraints from the existing PS are respected.

This objective is only one view. The product should also show a multi-dimensional scenario comparison for taxes, fees, liquidity, guarantee / benefit impacts, portfolio drift and uncertainty. Do not collapse suitability or legal eligibility into an opaque single friction score.

A sensible first version is a deterministic rules-and-calculation engine with scenario enumeration / constrained optimization. Predictive models for delay or success are out of scope until suitable historical data is available.

## 7. Proposed module architecture

1. **Input adapter:** consumes existing PS household / account / position / tax-lot / portfolio data.
2. **Portability rules layer:** maps position attributes, firm support and product constraints to route eligibility.
3. **Route generator:** creates feasible position-level disposition options.
4. **Consequence calculator:** computes tax, fees, penalties, benefits, liquidity and timing effects.
5. **Scenario engine / optimizer:** combines position routes under household constraints.
6. **Portfolio impact adapter:** calls or reuses existing PS portfolio / retirement analysis.
7. **Explanation and review output:** generates advisor-facing scenario tables, reasons, assumptions and exception flags.

## 8. Minimum output specification

### Position-level table
- Position / product
- Value and account type
- Portability status
- Feasible routes
- Selected route in each scenario
- Estimated tax / fees / penalties (separate fields)
- Benefit / guarantee warning
- Timing range (if supported)
- Confidence, data gaps and review flag

### Household-level comparison
- Scenario name
- Assets moved in-kind / alternate rail / BOR / liquidated / retained / deferred
- Estimated one-time cost and tax range
- Portfolio allocation and concentration after transition
- Liquidity / income implications
- Held-away asset value and reason
- Key trade-offs and review requirements

## 9. Prototype and validation plan

1. Build a synthetic mixed-asset household dataset with equities / ETFs, mutual funds, annuity, private investment and multiple account registrations.
2. Define a versioned, inspectable portability rules table; do not rely on an LLM to decide legal or operational eligibility.
3. Implement route feasibility and route-specific calculators with explicit assumptions.
4. Generate a small set of feasible household scenarios.
5. Reuse the existing PS portfolio calculations to compare post-transition outcomes.
6. Test edge cases: missing cost basis, stale values, unsupported product, partial transfer, taxable vs retirement account, annuity BOR vs surrender, issuer consent, retained asset, and contradictory firm rules.
7. Validate calculations against hand-worked examples and specialist review.
8. Present the concept and prototype output to the problem-statement owner / transition specialists to test whether it adds decision value beyond current tools.

## 10. Success criteria for a concept / pilot

Measure whether the feature:
- Correctly identifies feasible routes on a reviewed test set.
- Makes assumptions, data gaps and confidence visible.
- Produces reproducible tax / fee calculations against hand-worked cases.
- Shows household-level consequences that are not visible in a position-only transfer status.
- Reduces the time required to prepare an advisor-reviewed disposition plan (only measure after a baseline is established).
- Preserves client suitability and permits a documented retain / defer recommendation.

Do not claim a client-retention uplift, AUM-retention uplift or fixed time saving without baseline and outcome data.

## 11. Explicit non-goals

- Replacing the existing PS or its portfolio / financial-planning engine.
- ACATS or other transfer execution.
- Advisor onboarding, account opening, e-signature, document collection or task tracking.
- Generic NIGO detection or transfer-status dashboards.
- Predicting client attrition.
- Automatically recommending insurance replacement, annuity surrender or tax actions.
- Maximizing assets transferred regardless of client outcome.

## 12. Open validation items

The design can be specified without resolving the informal retention statistic. The material questions now are:
1. Which exact existing PS data structures and calculators can this module consume?
2. What position-level portability and product data can be obtained at decision time?
3. What route decisions do transition specialists currently make manually?
4. Can a specialist provide one anonymized mixed-asset case, including the available route choices and relevant costs / restrictions?
5. Which household-level comparisons are currently missing from the advisor's workflow?

## 13. Decision boundary

The add-on is approved as a **conceptual design direction**, not as a claim that LPL lacks the capability or as authorization for production implementation. The next work should refine inputs, route rules, calculations and outputs against one anonymized case and the existing PS specification. Do not introduce adjacent product ideas unless the problem-statement owner explicitly changes the scope.
