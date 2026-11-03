# Initial Architecture

## Product shape

AO-Tax-Engine is an assessment-support system for Assessing Officers. It is not an ITR filing application.

## Logical components

- **Frontend:** React-based user interface for case intake, manual data entry, computation review and assessment workflow.
- **Backend API:** Python API layer responsible for validation, persistence orchestration and access control.
- **Calculation core:** Deterministic Python package using decimal-safe arithmetic. Shared by online and offline editions.
- **Evidence and utility laboratory:** Read-only official utility archive, metadata, extracted workbook structure, formula/dependency evidence and differential test fixtures.
- **Persistence:** Relational database with explicit audit history and separation of source submissions, proposed adjustments and final assessment outcomes.
- **Offline edition:** Windows desktop shell around the same calculation core. It must not fork or duplicate tax logic.

## Core domain boundaries

Keep these concepts distinct:
- taxpayer/assessee identity and assessment case;
- return as filed and figures reported therein;
- source documents and evidence;
- proposed additions/disallowances;
- confirmed additions/disallowances;
- deletions and exclusions;
- returned, accepted and assessed income;
- tax computation and interest computation;
- penalty proceedings.

## Calculation design

- No tax computation in frontend code.
- No LLM-based calculation.
- Use explicit regime, assessment year, ITR form and utility-version context.
- Every calculation result should retain inputs, outputs, rule identifiers, source provenance and engine version.
- Utility-covered behavior must be validated against the corresponding official utility.
- Uncovered behavior must be separately identified, supported by legal authority and approved before implementation.

## Delivery phases

1. Repository and engineering foundation.
2. Utility inventory and workbook analysis.
3. Calculation domain model and deterministic engine.
4. AO workflow, including special-rate income and assessment adjustments.
5. Web application and offline Windows shell.
6. Independent validation, security review and controlled release.

## Open decisions

Do not silently decide database hosting, authentication provider, deployment platform, desktop packaging technology or long-term data-retention policy. Record options and trade-offs for product-owner approval before committing to a paid or externally hosted dependency.
