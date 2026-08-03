# 06 — Risk Analysis

## Status

This risk analysis applies to the planned MVP implementation. The project is currently in **Concept Phase**.

## Technical Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Transaction format complexity | Parser may fail on valid transaction variants. | Start with a clearly documented accepted input format and expand through fixtures. |
| Incorrect instruction decoding | Users could receive inaccurate explanations. | Use deterministic layouts, typed schemas, known examples, and tests for every supported instruction type. |
| Token decimals and account metadata ambiguity | Amounts may be hard to render correctly without mint context. | Document required metadata, fetch only necessary public chain data if needed, and show uncertainty explicitly. |
| AI hallucination | Explanation may overstate transaction effects. | Constrain AI to decoded facts and surface deterministic facts alongside prose. |
| Unsupported programs in real transactions | MVP may not explain complex dApp transactions fully. | Explicitly flag unknown instructions and avoid broad claims. |
| Authentication integration delays | Web MVP access flow may take longer than expected. | Use a standard managed auth provider and keep auth separate from wallet logic. |

## Project Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Scope creep into wallet/token scanning | MVP delivery could slip. | Keep out-of-scope list visible in planning and milestones. |
| Overpromising safety guarantees | Reviewer/user expectations may be misaligned. | Use "explain, don't decide" language throughout product and docs. |
| Four-week timeline compression | Reduced polish or test coverage. | Prioritize deterministic decoder correctness before UI polish. |
| Lack of production implementation at application time | Reviewers may need clarity on readiness. | Provide honest concept-phase documentation and a concrete implementation plan. |

## Assumptions

- MVP users can provide serialized transaction data for explanation.
- Initial scope is limited to System Program and SPL Token instructions listed in the brief.
- Email/social login can be implemented using a standard provider.
- AI output can be constrained to deterministic facts through prompt design and response validation.
- Grant period is approximately four weeks.

## Dependencies

- Solana JavaScript tooling for transaction parsing.
- SPL Token instruction layouts and token account metadata.
- AI provider API for explanation generation.
- Hosting and authentication provider for the web interface.
- Fixture transactions for supported instruction types.

## Risk Priority

The highest-priority risk is incorrect deterministic decoding. If the system cannot establish reliable facts, the AI explanation layer should not be allowed to compensate through inference. Decoder correctness comes before prose quality.
