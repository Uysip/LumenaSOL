# 05 — Milestones

## Status

These milestones describe planned grant work. They are not completed implementation claims.

## Milestone 1 — Decode Foundation

### Deliverables

- MVP project structure established.
- Transaction parsing entry point created.
- Normalized result schema defined.
- Unknown instruction handling added.

### Success Criteria

- A transaction can be parsed into an instruction list.
- Unsupported instructions are represented explicitly.
- The project has a repeatable local development setup.

### Checklist

- [ ] Project dependencies selected and installed.
- [ ] Decode result types defined.
- [ ] Transaction input validation implemented.
- [ ] Instruction enumeration implemented.
- [ ] Unknown instruction output implemented.

## Milestone 2 — Supported Instruction Decoding

### Deliverables

- System Program SOL transfer decoder.
- SPL Token transfer decoder.
- SPL Token approval decoder.
- Fixture-based decoder tests.

### Success Criteria

- Supported instruction types decode into structured facts.
- Decoding behavior is covered by tests and sample fixtures.
- Unsupported instructions are not hidden.

### Checklist

- [ ] System transfer decoding works.
- [ ] SPL Token transfer decoding works.
- [ ] SPL Token approval decoding works.
- [ ] Fixtures added for all supported instruction families.
- [ ] Decoder tests pass locally.

## Milestone 3 — Approval Analysis and AI Explanation

### Deliverables

- Rule-based detection for unusually large or unlimited token approvals.
- Structured analysis output.
- Constrained AI explanation prompt.
- Plain-English explanation response format.

### Success Criteria

- Approval warnings are generated from deterministic rules.
- AI explanations map to decoded facts without inventing behavior.
- Unknown instructions are described as unknown.

### Checklist

- [ ] Approval warning threshold documented.
- [ ] Unlimited approval detection implemented.
- [ ] AI prompt contract implemented.
- [ ] Explanation output validated against fixture cases.

## Milestone 4 — Web MVP and Grant Delivery

### Deliverables

- Simple web interface.
- Email/social login.
- Transaction input flow.
- Explanation result view.
- Accurate README and limitation documentation.

### Success Criteria

- A reviewer can run or access the MVP and explain supported transaction examples.
- Signing remains outside LumenaSOL.
- Documentation matches actual implemented behavior.

### Checklist

- [ ] Web UI accepts transaction input.
- [ ] Decoded facts are displayed.
- [ ] Plain-English explanation is displayed.
- [ ] Login works for intended access flow.
- [ ] No wallet connection is required for explanation.
- [ ] Final docs updated with implemented scope and known limitations.

## Overall MVP Completion Definition

The MVP is complete when LumenaSOL can explain supported System Program and SPL Token transaction examples in plain English, while clearly identifying unsupported instructions and maintaining non-custodial, no-wallet-connection boundaries.
