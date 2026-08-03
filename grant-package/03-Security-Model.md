# 03 — Security Model

## Status

This security model describes planned MVP constraints for a concept-phase project. It is not a statement that a production security implementation already exists.

## Security Objective

LumenaSOL's objective is to improve transaction understanding before signing. It is not a guarantee that a transaction is safe, and it is not a replacement for wallet security, dApp audits, or user judgment.

## Trust Assumptions

- Users provide transaction data they want explained.
- Deterministic decoding logic is the source of truth for known instruction types.
- The AI provider is used only for language generation from verified facts.
- Wallets remain responsible for signing, key custody, and transaction submission.
- Unsupported instructions may exist and must be disclosed rather than guessed.

## Threat Model

| Threat | Planned Mitigation |
|---|---|
| AI hallucination about transaction behavior | AI receives structured facts, not authority; prompt requires unknowns to remain unknown. |
| Mis-decoding supported instructions | Build typed decoders, fixture tests, and known transaction examples during MVP implementation. |
| Unsupported instruction hidden from user | Unknown instructions are explicitly surfaced in the structured result and explanation. |
| User assumes explanation equals safety guarantee | Product copy and UI should state that LumenaSOL explains, not approves. |
| Private key or wallet credential exposure | Product does not request private keys, seed phrases, or wallet login. |
| Custody or signing risk | LumenaSOL does not sign, execute, or submit transactions in the MVP. |
| Privacy leakage to AI provider | Send only the minimum structured data needed for explanation; avoid sending secrets because none are required. |
| Over-broad token approvals | Rule-based detection flags unusually large or unlimited approvals. |

## Deterministic-First Design

The core security decision is that deterministic decoding precedes AI generation. The AI layer is intentionally downstream from decoding and analysis.

The AI layer should not:

- Decode raw binary transaction data by itself.
- Infer unsupported instruction effects.
- Override deterministic analysis results.
- Produce a simple safe/unsafe verdict.
- Ask for or handle wallet credentials.

## Privacy Model

The MVP should avoid collecting information that is not required to explain a transaction.

Expected data categories:

- Transaction payload supplied by the user.
- Basic login identifier for email/social auth.
- Generated explanation output.

Not expected:

- Private keys.
- Seed phrases.
- Custodial wallet credentials.
- Wallet connection session data for explanation.

## Non-Custodial Approach

LumenaSOL is not a wallet. It does not hold assets, custody keys, or initiate signing. Users sign only inside their own wallet after reviewing the explanation.

## Limitations

- MVP coverage is limited to System Program transfers, SPL Token transfers, and SPL Token approvals.
- Unsupported program behavior may be material and must be disclosed.
- Token and wallet reputation analysis are out of scope.
- A transaction may have effects that require broader protocol-specific decoding not available in v0.1.
- Plain-English explanation can improve comprehension but cannot eliminate signing risk.

See also [02-Architecture.md](./02-Architecture.md) for the planned component boundaries.
