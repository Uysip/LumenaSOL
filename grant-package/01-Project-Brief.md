# 01 — Project Brief

## Project

**LumenaSOL** is an AI-powered transaction intelligence layer for Solana. It is designed to decode a specific transaction and explain it in plain English before a user signs it.

LumenaSOL is currently in **Concept Phase**. The repository contains project positioning, intended scope, and architecture documentation. No production implementation exists yet.

## Problem Statement

Solana transaction prompts expose technically accurate data, but most users cannot interpret program IDs, account metas, serialized instruction data, authority changes, or token approval semantics quickly enough to make an informed signing decision.

Current wallet prompts often answer: "what object am I being asked to sign?" LumenaSOL is intended to answer: "what will this transaction do?"

## Vision

LumenaSOL's long-term vision is to become a pre-signature explanation layer for Solana transactions. The system should make deterministic transaction facts understandable without taking custody, replacing the user's wallet, or pretending to determine universal safety.

The MVP is deliberately narrow: deterministic decoding first, AI translation second, and user judgment last.

## Goals

### MVP Goals

- Decode System Program SOL transfers.
- Decode SPL Token transfers.
- Decode SPL Token approvals.
- Detect unusually large or unlimited token approvals.
- Generate plain-English explanations from verified decoded facts.
- Provide a simple web interface for transaction explanation.
- Support email/social login.
- Avoid wallet connection requirements for explanation.
- Keep transaction signing inside the user's own wallet.

### Non-Goals

- No token safety scoring.
- No wallet reputation analysis.
- No browser extension.
- No SDK in the MVP.
- No MCP server in the MVP.
- No custody, transaction signing, private key handling, or wallet replacement.

## Product Philosophy

LumenaSOL follows a deterministic-first philosophy:

1. Decode transaction data into structured facts.
2. Apply explicit rules for known transaction patterns.
3. Flag unsupported or unknown instructions instead of guessing.
4. Use AI only to translate verified facts into readable language.
5. Leave the final decision to the user.

The AI layer must not invent transaction effects. If deterministic decoding cannot establish a fact, the explanation should say so.

## Target Users

- Solana users who want to understand a pending transaction before signing.
- Consumer dApp users exposed to unfamiliar token transfer or approval prompts.
- Builders who want a reference model for deterministic transaction explanation.
- Security-conscious users who prefer readable transaction context without connecting a wallet to another tool.

## Differentiators

LumenaSOL is not positioned as a general-purpose wallet scanner or token scanner. Its differentiation is explaining a specific transaction in context.

| LumenaSOL | Not LumenaSOL |
|---|---|
| Specific transaction explanation | General wallet risk scoring |
| Deterministic decode before AI | Free-form AI speculation |
| Pre-signature information layer | Wallet, custodian, or signer |
| Plain-English interpretation of known facts | Universal safe/unsafe verdict |
| Focused v0.1 scope | Broad scanner or extension platform |

## Current Status

The project is in **Concept Phase**. Planning and architecture are complete enough to begin implementation during the grant period, but no functional transaction decoder, AI explanation service, authentication flow, or web interface currently exists.

See also:

- [02-Architecture.md](./02-Architecture.md)
- [04-Implementation-Plan.md](./04-Implementation-Plan.md)
- [05-Milestones.md](./05-Milestones.md)
