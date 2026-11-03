# AO-Tax-Engine Agent Instructions

## Mission

Build an Assessing Officer-oriented tax computation and assessment-support application. Do not turn this into a taxpayer return-filing product.

## Authority hierarchy for tax behavior

1. Applicable official Income Tax Department Excel utility, including its version-specific formulas, validations, restrictions and behavior.
2. Applicable legislation, rules, notifications, circulars and binding judicial authorities for matters not covered by the utility.
3. Explicitly approved product decisions recorded by the product owner.

Never invent or silently infer a tax rule. If authoritative evidence is missing or conflicting, stop that implementation path, document the gap and request a decision.

## Calculation safety

- Tax computation must be deterministic and use decimal-safe arithmetic.
- LLMs must not calculate tax, choose rates, infer eligibility or generate statutory mappings.
- Keep the Income-tax Act, 1961 regime separate from the Income-tax Act, 2025 regime.
- Keep returned income, proposed additions, confirmed additions, deletions/exclusions, accepted income and assessed income as distinct concepts.
- Proposed additions are not automatically confirmed additions.
- Keep penalty proceedings and penalty calculations separate. Never trigger them automatically.
- Model Sections 234A, 234B, 234C and 234D separately, with provenance for every rule.

## Official utility evidence

For each utility, preserve the original workbook read-only and record:
- official source URL;
- assessment year and ITR form;
- utility version and download date;
- SHA-256 checksum;
- worksheets, including hidden worksheets;
- formulas, named ranges, validations, macros and external links;
- extracted input/output fields and dependency relationships.

Where a utility covers a calculation, reproduce its behavior and differentially test against its outputs. Mark uncovered cases explicitly for statutory analysis and product-owner approval.

## Engineering workflow

- Inspect before editing. Write a bounded plan for non-trivial tasks.
- Use a dedicated branch per task. Do not work concurrently on the same files without coordination.
- Add tests with implementation. Run relevant tests and report exact commands and results.
- Do not claim a test passed unless it was actually executed.
- Keep changes small, reviewable and traceable to an issue/task.
- Do not commit secrets, API keys, taxpayer data or real assessment records.
- Use synthetic fixtures only.
- No paid APIs, paid model fallback, paid hosting or paid dependencies without explicit product-owner approval.
- Never merge to `main`, publish a release or deploy without explicit product-owner approval.

## First implementation boundary

Until the official utility inventory and architecture are reviewed, do not implement statutory tax formulas, rates, deductions, special-rate mappings or interest calculations. The initial work may establish repository structure, developer tooling, interfaces, evidence schemas and tests that do not encode tax law.
