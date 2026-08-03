# 04 — Implementation Plan

## Status

This plan covers the intended four-week MVP implementation period. The repository is currently in **Concept Phase** and does not yet contain a working decoder, web app, authentication flow, or AI explanation layer.

## MVP Scope

The MVP will include only:

- Decode System Program transfers.
- Decode SPL Token transfers.
- Decode SPL Token approvals.
- Detect unusually large or unlimited token approvals.
- Generate plain-English explanations from deterministic facts.
- Provide a simple web interface.
- Support email/social login.
- Require no wallet connection for explanation.
- Keep signing inside the user's own wallet.

## Week 1 — Project Foundation and Deterministic Decode Skeleton

### Goals

- Establish implementation structure for the web app and core decoder.
- Define transaction input format and normalized result schema.
- Implement initial transaction parsing and instruction enumeration.

### Deliverables

- Working project setup for the MVP codebase.
- Typed decode result schema.
- Parser that accepts supported serialized transaction input.
- Unknown instruction representation.
- Initial fixtures for System Program and SPL Token transaction examples.

### Completion Criteria

- The system can parse a transaction envelope and list instructions.
- Unsupported instructions are preserved as explicit unknown records.
- Development setup is documented.

## Week 2 — Supported Program Decoding and Rule-Based Analysis

### Goals

- Implement deterministic decoders for MVP instruction types.
- Add approval analysis rules.
- Create tests around decoding behavior.

### Deliverables

- System Program transfer decoder.
- SPL Token transfer decoder.
- SPL Token approval decoder.
- Rule for unusually large or unlimited approvals.
- Unit tests and fixture-based validation for supported cases.

### Completion Criteria

- Supported instruction types decode into structured facts.
- Unknown instructions remain visible.
- Approval warnings are generated from explicit rules rather than AI inference.

## Week 3 — AI Explanation Layer and Web Interface

### Goals

- Connect structured facts to constrained plain-English explanation generation.
- Build a simple user interface for submitting a transaction and reading the result.
- Add email/social authentication.

### Deliverables

- Constrained AI explanation prompt and response contract.
- Backend route or service for explanation generation.
- Web UI for transaction input, decoded facts, warnings, and explanation.
- Email/social login integration.
- Error states for invalid transactions and unsupported instructions.

### Completion Criteria

- A user can submit transaction data and receive a readable explanation for supported instructions.
- Deterministic decoded facts are visible independently of the AI prose.
- AI failure does not prevent deterministic facts from being displayed.

## Week 4 — Hardening, Review, Documentation, and MVP Delivery

### Goals

- Improve reliability, clarity, and security posture.
- Prepare the MVP for reviewer evaluation.
- Document limitations honestly.

### Deliverables

- End-to-end happy-path flow for supported transaction types.
- Regression tests for decoder fixtures.
- README/setup updates with accurate run instructions.
- Security and limitation notes in the product UI/docs.
- Final grant deliverable summary.

### Completion Criteria

- MVP demonstrates the planned supported transaction explanation flow.
- Documentation reflects actual implemented capabilities.
- Out-of-scope items remain excluded unless explicitly deferred for future work.

## Out-of-Scope During Grant MVP

- Token safety scoring.
- Wallet reputation analysis.
- Browser extension.
- SDK.
- MCP server.
- Custody or transaction signing.
