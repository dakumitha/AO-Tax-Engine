# AO-Tax-Engine

An Assessing Officer-oriented income-tax computation and assessment-support application.

## Product boundaries

- This is an Assessing Officer's computation application, not a taxpayer ITR filing application.
- The calculation engine must be deterministic. LLMs may assist with research, explanations and software engineering, but must never calculate or invent tax liability.
- Official Income Tax Department Excel utilities are the controlling computational reference wherever they cover a calculation, validation, restriction or workflow.
- Preserve separate legal regimes for the Income-tax Act, 1961 and the Income-tax Act, 2025.
- Begin with manual data entry. Document ingestion and OCR are later phases.
- The same Python calculation core must support the online application and offline Windows edition.

## Non-negotiable controls

1. No invented tax rates, thresholds, formulas, eligibility rules or statutory mappings.
2. Every implemented tax rule must have traceable authoritative provenance and tests.
3. Proposed additions must remain distinct from confirmed additions and assessed income.
4. Penalty proceedings and computations must remain separate from assessment computation and must not be triggered automatically.
5. Never place taxpayer-identifiable or confidential assessment data in public repositories, public agent prompts or external model providers.
6. No paid API, model fallback, hosting or dependency without explicit approval.
7. No automatic merge to `main` or production deployment.

## Initial development sequence

1. Repository governance and architecture.
2. Official utility inventory and read-only evidence archive.
3. Utility workbook inspection and formula/dependency extraction.
4. Deterministic calculation engine and differential tests.
5. AO assessment workflow and special-rate income schedule.
6. Web and offline Windows interfaces.
7. Independent review, security testing and release validation.

See [AGENTS.md](AGENTS.md) and [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).
