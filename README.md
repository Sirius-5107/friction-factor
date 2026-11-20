# Friction Factor
## Inter IIT LPL Financials — Research repository

This repository is the persistent research log for the proposed add-on feature around advisor transitions, asset portability and transition-related financial friction.

## Current research dossiers

- [Portability-Adjusted Transition Optimizer](research/portability-adjusted-transition-optimizer.md) — problem framing, public evidence, LPL's existing capabilities, ACATS / non-ACATS portability taxonomy, proposed product workflow, quantitative framework, risks, open questions and research plan.
- [Transfer Rails & Regulatory Updates](research/transfer-rails-and-regulatory-updates.md) — DTCC specialist rails (Fund/SERV, I&RS, AIP, OCC), partial transfers, annuity broker-of-record processing, FINRA consent boundary and proposed position-level data model.

- [Add-on Feature Design](research/add-on-feature-design-spec.md) — fixed-scope product definition, synthetic household walkthrough, module architecture, optimization formulation, inputs, outputs, prototype plan and non-goals.\n\n## Stage 1 validation

- [Stage 1 — Validate the LPL Capability Gap](research/stage-1-capability-gap-validation.md) — public capability map, retention-metric clarification, gap matrix, interview questions, evidence requests and go/no-go criteria.


### Stage 1 follow-up findings

- LPL's *Overcoming Transition Hurdles* white paper cites a February 2014 survey: 59% of surveyed advisors fell in the 75%–100% client-retention band. This is a possible source of an informal ~80% claim, but not an 80% average and not confirmed as the senior's source.
- LPL's Q3 2026 83% Commonwealth figure is asset retention; management attributed the reduction from ~85% signed-advisor stage to a small number of signed advisors deciding not to stay—not to transfer paperwork.
- Public sources identify multiple causes (advisor/client choice, relationship and communication, incumbent multi-product relationships, product portability, legal/privacy and paperwork), but provide no cause-level percentages.
- Public materials still do not establish whether LPL internally compares asset-level transfer / liquidate / retain / defer economics at household level. An anonymized mixed-asset case and internal capability confirmation are still required.

## Current working hypothesis

Build an **analytical decision-support layer**, not another onboarding or transfer execution tool.

The proposed layer would compare feasible ways to handle each household asset during an advisor transition — transfer in-kind, use an alternate transfer route, change broker of record, liquidate and transfer cash, retain at the old institution, or defer — and quantify the resulting tax, fee, liquidity, guarantee, portfolio and financial-planning consequences.

## Important research discipline

- Separate verified facts, company claims, team-reported inputs and hypotheses.
- Do not repeat the reported "80% client retention" figure as fact until its denominator, source and time horizon are confirmed.
- LPL publicly reports a 45-day average advisor transition in 2026 and 90% of AUM transitioned by the second month. This is not the same as an account-level ACATS timeline or client-retention rate.
- LPL already publicly describes an onboarding portal, transition specialists, CAT, IAT, repapering automation and ClientWorks. Avoid proposing duplicate workflow features.
- ACATS integrates with specialist processing rails; do not reduce the model to a binary transferable / non-transferable flag.
- The potential gap — household-level financial scenario analysis for difficult / partially transferable assets — remains unvalidated.
- Keep client suitability central. Retaining an asset at the old institution can be the correct outcome.

## How to continue this research

1. Read the current dossiers before starting a new chat or adding a new feature idea.
2. Add sources with publication dates and explain exactly which claims they support.
3. Mark assumptions and unknowns explicitly.
4. Update the relevant dossier's change log when material findings are added.
5. Do not begin implementation until the product gap is confirmed with LPL / the problem-statement owner.

Last updated: 20 November 2026 (Stage 1 desk research added).
