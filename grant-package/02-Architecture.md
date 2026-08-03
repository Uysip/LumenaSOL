# 02 — Architecture

## Status

This architecture describes the planned MVP. It is not an implemented system yet. LumenaSOL is currently in **Concept Phase**.

## High-Level System

```text
User-provided transaction
        |
        v
Input validation and transaction parsing
        |
        v
Deterministic decoder
  - System Program transfer decoder
  - SPL Token transfer decoder
  - SPL Token approval decoder
        |
        v
Structured transaction facts
        |
        v
Rule-based analysis
  - transfer summary
  - approval scope
  - large/unlimited approval detection
  - unknown instruction flagging
        |
        v
AI explanation layer
  - constrained prompt
  - facts-only translation
  - no signing authority
        |
        v
Plain-English explanation in web UI
```

## Planned Components

### Web Interface

A simple web app will accept transaction data for explanation. The MVP interface is expected to support a paste/upload style flow rather than requiring wallet connection.

Responsibilities:

- Accept serialized transaction input.
- Show parse/decode status.
- Display deterministic decoded facts.
- Display AI-generated plain-English explanation.
- Surface warnings for unknown instructions or unusually broad approvals.

### Authentication

The MVP plans to support email/social login. Authentication is for product access and basic user continuity, not for wallet authorization.

No wallet connection is required for explanation in the planned MVP.

### Core Decode Engine

The core engine will be responsible for deterministic transaction parsing and instruction decoding.

Initial supported instruction families:

- System Program SOL transfers.
- SPL Token transfers.
- SPL Token approvals.

The core engine should return structured, typed facts rather than prose.

### Rule-Based Analysis Layer

The analysis layer will operate only on decoded structured facts. It will identify:

- Asset movement direction and amount when available.
- Approval delegate and allowance scope when available.
- Unusually large or unlimited token approvals.
- Unsupported programs or unsupported instruction types.

### AI Explanation Layer

The AI layer will convert structured facts into readable explanations. It should not receive authority to sign, submit, mutate, or execute transactions.

The intended prompt contract is:

- Input: deterministic facts and analysis flags.
- Output: concise human-readable explanation.
- Constraint: do not infer unsupported behavior.
- Constraint: explicitly mention unknown or unsupported instructions.

## Data Flow

1. User provides transaction data through the web interface.
2. Backend or local decode service validates the input format.
3. Decoder parses the transaction message and extracts supported instructions.
4. Unsupported instructions are included as unknown/unsupported records.
5. Analysis layer derives rule-based warnings from decoded facts.
6. AI explanation layer receives the structured facts and flags.
7. UI presents both deterministic facts and plain-English explanation.
8. User returns to their own wallet to approve or reject the transaction.

## Deterministic Decoding Pipeline

The planned pipeline prioritizes correctness over coverage:

1. Parse transaction envelope.
2. Enumerate instructions.
3. Match instruction program IDs against supported programs.
4. Decode known instruction layouts.
5. Normalize amounts, token accounts, owner/delegate fields, and recipients where available.
6. Record unsupported instructions explicitly.
7. Emit a structured result object.

Unknown instructions must never be silently ignored.

## Security Boundaries

LumenaSOL is intended to be non-custodial and non-signing.

Security boundaries:

- No private keys or seed phrases are accepted.
- No wallet signing is performed by LumenaSOL.
- No transaction submission is performed by LumenaSOL in the MVP.
- AI cannot alter decoded facts.
- AI cannot classify unknown data as safe.
- The user signs only in their own wallet.

## Failure Modes

If decoding fails, the system should return a clear parse/decode error.

If AI explanation fails, the deterministic decoded output should still be shown.

If a transaction contains unsupported instructions, the system should explain that not all behavior can be decoded within MVP scope.

See also:

- [03-Security-Model.md](./03-Security-Model.md)
- [04-Implementation-Plan.md](./04-Implementation-Plan.md)
