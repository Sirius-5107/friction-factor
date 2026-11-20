# Transfer Rails & Regulatory Updates
## Research addendum — Inter IIT LPL Financials

**Date:** 20 November 2026  
**Related dossier:** [Portability-Adjusted Transition Optimizer](portability-adjusted-transition-optimizer.md)  
**Purpose:** Refine the asset portability taxonomy using current DTCC, SEC and FINRA materials.

---

## 1. Key finding: do not classify assets as simply "ACATS" or "non-ACATS"

DTCC's current ACATS product description explicitly says ACATS supports a broad range of asset types, including equities, bonds, unit investment trusts, mutual funds, options, annuities, alternative investments and cash. It integrates with specialist services:

| Asset / processing need | Related DTCC service |
|---|---|
| General account transfer orchestration | ACATS |
| Mutual fund re-registration | Fund/SERV |
| Insurance / annuity assets | Insurance & Retirement Solutions (I&RS) |
| Private market / alternative investment assets | Alternative Investment Product (AIP) |
| Listed options | Options Clearing Corporation (OCC) |

Source: DTCC ACATS product page: https://www.dtcc.com/products-and-services/clearing-settlement-services/equities-clearing/acats

### Product implication

The engine should not use a binary field like transferable = yes/no as its core data model.

It should instead model:
- Asset eligibility.
- Required processing rail / service.
- Delivering-firm participation.
- Receiving-firm participation and product support.
- Asset-specific and account-specific restrictions.
- Required customer / issuer / carrier instructions.
- Expected processing path and exception conditions.
- Confidence, source and effective date.

The question is not just "Can this asset move?" It is "Through which route, subject to whose eligibility and approval, with what financial and timing consequences?"

---

## 2. Partial transfers are an important design case

FINRA Regulatory Notice 22-19 explains that Rule 11870 covers transfers of all or specifically designated parts of customer securities accounts. It recognizes non-transferable assets, including third-party products for which the receiving firm lacks the necessary relationship or arrangement to hold the asset. Customers must receive information / be asked for instructions about disposition of certain non-transferable assets.

Source: FINRA Regulatory Notice 22-19 (8 August 2022): https://www.finra.org/sites/default/files/2022-08/Regulatory-Notice-22-19.pdf

The DTCC / ACATS process also provides for asset-level review: the receiving firm can accept all assets, reject one or more assets where permitted and allow the remaining assets to transfer, request asset-list adjustments, or reject the account where permitted.

Source: SEC, NSCC filing (2026): https://www.sec.gov/files/rules/sro/nscc/2026/34-106751.pdf

### Product implication

Partial transfer is not an edge case to ignore. The model should represent a household where:
- Some positions transfer through standard ACATS.
- Some positions use specialist integrated rails.
- Some positions require a separate bilateral / issuer / carrier process.
- Some positions are excluded or retained.
- Some assets remain unresolved pending client instructions.

The household-level optimizer should then calculate the financial implications of the resulting mixed portfolio.

---

## 3. Annuity processing: important 2026 update

The SEC's 28 October 2026 notice concerning an NSCC filing describes ACATS functionality for Insurance & Retirement Products (I&RS), including annuities. ACATS / Insurance Processing Service (ACATS/IPS) automates changes in distributor of record when clients transfer brokerage accounts. It can facilitate representative-of-record and broker-identification changes within an annuity contract.

The 2026 filing proposes moving insurance product re-registration and confirmation processing from ACATS records into the I&RS service system. Under the described proposed workflow:
1. ACATS continues to initiate and submit insurance assets.
2. ACATS validates product / receiving-member eligibility.
3. The receiving member is notified that a broker-dealer-of-record change is needed.
4. The receiving member sends the change instruction to I&RS.
5. I&RS routes information to the insurance carrier.
6. The carrier confirms to I&RS, which notifies the receiving member.

Source: SEC Release 34-106751, filed 28 October 2026: https://www.sec.gov/files/rules/sro/nscc/2026/34-106751.pdf

**Caution:** The document is a notice of a proposed rule change that NSCC filed and the SEC published for comment; do not describe all proposed process changes as already fully implemented unless current DTCC operating documentation confirms this.

### Product implication

The model needs separate annuity route types:
- Broker / distributor / representative-of-record change through the relevant insurance processing service.
- Contract exchange / replacement.
- Surrender / cash-out.
- Retain current contract and servicing arrangement.

These are not economically equivalent. A broker-of-record change should not be assigned a surrender charge or assumed loss of contract guarantees merely because the advisor changes firms. Contract exchange / surrender analysis should only run when the client is actually considering changing or terminating the insurance contract.

---

## 4. FINRA Rule 11870 and the consent boundary

FINRA Regulatory Notice 26-03 (6 February 2026) consolidates guidance on negative consent for **bulk transfers or assignments** of customer accounts. It states the general position that a member must obtain affirmative customer consent or instruction to transfer or assign an account. Negative consent may be appropriate only in limited bulk-transfer situations, such as certain firm closures, business-line exits, mergers, clearing relationship changes and other specified circumstances.

The notice also distinguishes:
- Individual customer account transfers under Rule 11870, generally initiated by the customer through an instruction to the receiving firm.
- Bulk transfers / assignments in limited circumstances.
- Assignments of the brokerage relationship without moving assets, which can also require affirmative consent in ordinary cases.

Source: FINRA Regulatory Notice 26-03 (6 February 2026): https://www.finra.org/sites/default/files/2026-02/Regulatory-Notice-26-03.pdf

### Product implication

Do not build a feature that assumes clients can be moved automatically or that uses negative consent as a way to improve advisor portability. The 2026 guidance concerns limited bulk-transfer circumstances, not a general shortcut for an individual advisor changing firms. Client authorization, applicable rules and firm compliance procedures remain essential.

The feature's role is to support transparent, client-beneficial analysis and preparation — not to bypass consent or transfer requirements.

---

## 5. Revised asset-route data model

Recommended first-pass schema for each position / contract:

| Field | Description |
|---|---|
| household_id | Household identifier |
| account_id | Source account |
| position_id | Security / contract position identifier |
| asset_identifier | CUSIP, ticker, fund identifier, contract number token, or other permitted identifier |
| asset_type | Equity, ETF, mutual fund, bond, annuity, private fund, deposit, option, etc. |
| market_value | Current value and as-of date |
| registration_type | Individual, joint, IRA, trust, entity, etc. |
| cost_basis | Lot-level basis where relevant |
| candidate_rail | ACATS, Fund/SERV, I&RS / ACATS-IPS, AIP, OCC, bilateral / issuer, direct custodian, other |
| rail_eligibility | Eligible, conditional, ineligible, unknown |
| delivering_firm_support | Yes / no / unknown |
| receiving_firm_support | Yes / no / unknown |
| restrictions | Product / account / firm restrictions |
| required_action | Customer instruction, issuer consent, carrier confirmation, re-registration, liquidation, etc. |
| candidate_disposition | In-kind, alternate rail, retain, liquidate, defer, manual review |
| estimated_time_range | Only if supported by data / rules |
| estimated_cost | Route-specific estimate |
| confidence | High / medium / low |
| evidence_source | URL / rule / internal source |
| effective_date | Date the rule / eligibility evidence was checked |

This is a conceptual schema. Do not store real client identifiers or account numbers in a prototype; use synthetic or tokenized values.

---

## 6. Updated hypotheses and open questions

### New hypotheses
1. The strongest product gap may be **route-aware household economics**, not raw transferability classification.
2. Some assets that appear difficult to transfer may in fact have specialist DTCC processing rails; the issue may be eligibility, required data, firm participation, carrier / issuer confirmation or operational exception handling.
3. Partial transfers should be modeled as normal household scenarios, not as binary account-level success / failure.
4. Annuity transitions require careful distinction between distributor-of-record changes and actual contract replacements.
5. Client consent is a hard design constraint, not a friction variable to optimize away.

### Questions for LPL / transition specialists
1. Which specialist rails (Fund/SERV, I&RS / ACATS-IPS, AIP, OCC) are used in LPL's transition process, and which are supported end-to-end in its internal tools?
2. Does CAT / IAT / the onboarding portal show route-level asset eligibility, or mainly gather data and orchestrate account opening / repapering?
3. Does LPL produce an asset-by-asset disposition plan before the transition?
4. Does it compare the economics of moving versus retaining an asset?
5. How are partial transfers and residual positions surfaced at household level?
6. For annuities, how are broker-of-record changes distinguished from replacement / surrender decisions?
7. What proportion of delayed AUM is explained by carrier / issuer processing versus client instructions, product ineligibility, missing data or other exceptions?

---

## 7. Updated assessment

| Finding | Assessment |
|---|---|
| ACATS is broader than simple stocks-and-bonds transfer | Confirmed by DTCC |
| ACATS integrates specialist services for mutual funds, annuities, alternatives and options | Confirmed by DTCC |
| Some positions may be excluded while remaining assets transfer | Supported by FINRA / SEC transfer guidance |
| Annuity broker-of-record processing can occur through ACATS / I&RS | Confirmed in SEC's 2026 NSCC filing |
| 2026 I&RS process changes are all fully implemented | Not established by the filing alone |
| Negative consent is a general workaround for advisor moves | False; FINRA guidance concerns limited bulk-transfer cases |
| Household-level route economics is an LPL product gap | Still unverified |

---

## 8. Additional sources

1. **DTCC — Automated Customer Account Transfer Service (ACATS)**  
   https://www.dtcc.com/products-and-services/clearing-settlement-services/equities-clearing/acats  
   Current overview of ACATS asset coverage and integrations with Fund/SERV, I&RS, AIP and OCC.

2. **FINRA Regulatory Notice 22-19** (8 August 2022)  
   https://www.finra.org/sites/default/files/2022-08/Regulatory-Notice-22-19.pdf  
   Rule 11870, partial transfers, non-transferable assets and third-party product arrangements.

3. **SEC Release 34-106751 / NSCC-2026-011** (28 October 2026)  
   https://www.sec.gov/files/rules/sro/nscc/2026/34-106751.pdf  
   ACATS and I&RS processing for insurance / retirement products, including annuity distributor-of-record changes and proposed process enhancements.

4. **FINRA Regulatory Notice 26-03** (6 February 2026)  
   https://www.finra.org/sites/default/files/2026-02/Regulatory-Notice-26-03.pdf  
   Negative consent for limited bulk transfers / assignments; distinction from ordinary individual transfers.

---

## 9. Change log

- **2026-11-20:** Added DTCC specialist-rail mapping (Fund/SERV, I&RS, AIP, OCC); clarified partial transfers; incorporated the October 2026 NSCC / SEC filing on annuity processing; documented FINRA 2026 negative-consent guidance and its limited bulk-transfer scope; proposed route-aware position-level data model.
