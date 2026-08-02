# LumenaSOL

**AI-powered transaction intelligence for Solana: plain-English explanation of a transaction, before you sign it.**

*Goal:* take a Solana transaction, decode what it actually does, and return a plain-language explanation — what moves, what authority is granted, what programs are involved, and what looks unusual — before a wallet is asked to sign.

> ### Status: concept phase. No implementation exists yet.
>
> This describes the intended product, **not** current capability.
>
> **Works today:** problem definition, product scope, architecture design, and this documentation set.
>
> **Does not exist yet:** transaction decoding, the AI explanation layer, the web app, and any deployed infrastructure. Nothing in this repository can currently explain a real transaction.
>
> See **[docs/IMPLEMENTATION_STATUS.md](docs/IMPLEMENTATION_STATUS.md)** for the full breakdown.

---

## Why

Solana wallets show users what a transaction *is*, not what it *does*. A signing prompt lists program IDs, instruction data, and account lists — technically complete, practically unreadable. Most users approving a transaction cannot say with confidence what asset moves, where it goes, or what permission they're granting.

The common fix is asking users to "be careful" or read a warning banner. That isn't an understanding model — a user who can't parse the underlying data can't meaningfully evaluate a warning about it either.

LumenaSOL puts an explanation layer between the transaction and the signature. **Deterministic decoding establishes the facts. AI translates those facts into plain language. The user decides.** The AI layer never signs, never executes, and never overrides the user's own judgment — it only makes the existing data legible.

## Product philosophy

- LumenaSOL **never** stores private keys, seed phrases, or wallet credentials. There is no code path that could hold one.
- LumenaSOL **never** signs or executes a transaction on a user's behalf. Signing always happens in the user's own wallet.
- AI explanation is generated only from **deterministically decoded, verified transaction data** — never from unconstrained inference about what a transaction "probably" does.
- If the AI layer is unavailable, the deterministic decode output should still be usable on its own — degraded readability, not degraded correctness.
- **Explain, don't decide.** LumenaSOL surfaces what a transaction does and flags what's unusual about it. It doesn't tell a user whether to approve it.

This is a pre-signature information layer, not a guarantee of transaction safety. It is not a security scanner and does not produce a standalone "safe / unsafe" score for tokens or wallets independent of a specific transaction.

## Current status

| Area | State |
|---|---|
| Problem definition, positioning, product scope | **Done** |
| Repository structure and documentation set | **Done** |
| Architecture design (decode → analyze → explain pipeline) | **In progress** |
| Transaction decoding (System Program, SPL Token) | **Not implemented** |
| Deterministic risk-flag rules | **Not implemented** |
| AI explanation layer | **Not implemented** |
| Web app (chat-style interface, no wallet connect required) | **Not implemented** |
| Deployment | **Not implemented** |

Nothing marked "Not implemented" has a working code path in this repository. This table is the single source of truth for project status — if other documents in this repo imply otherwise, this table is correct and they are stale.

Full breakdown: **[docs/IMPLEMENTATION_STATUS.md](docs/IMPLEMENTATION_STATUS.md)**.

## What it will check (v0.1 scope)

The first working version is scoped narrowly on purpose — one input type, two programs, no standalone scoring:

| Signal | What it means |
|---|---|
| Asset transfer direction and amount | What's actually moving, in and out |
| Token approval scope | Whether an approval is bounded or unlimited |
| Program identity | Which known program(s) the transaction interacts with |
| Unrecognized program or instruction | Flagged for explicit human attention rather than silently explained |

Wallet-level and token-level scoring (the kind of general "is this token safe" check tools like RugCheck already do well) is explicitly out of scope for v0.1. LumenaSOL's differentiation is explaining a specific transaction in context, not re-building a general-purpose scanner.

## Planned repository layout

```
LumenaSOL/
  README.md
  LICENSE
  ROADMAP.md
  CHANGELOG.md
  CONTRIBUTING.md
  SECURITY.md

  docs/
    PRODUCT.md               # Full product spec
    ARCHITECTURE.md          # Decode -> analyze -> explain pipeline design
    IMPLEMENTATION_STATUS.md # Live, authoritative status table
    IMPLEMENTATION_PLAN.md   # Milestone breakdown
    SECURITY_MODEL.md        # Trust boundaries, threat model
    AI_DESIGN.md             # Constraints on the AI explanation layer
    TECH_STACK.md            # Stack choices and rationale

  apps/web/                  # NOT IMPLEMENTED — reference web client
  packages/core/             # NOT IMPLEMENTED — deterministic decode/analysis engine
  packages/sdk/              # NOT IMPLEMENTED — future public SDK surface
  assets/                    # Brand and diagram source files
```

The core decoding/analysis logic is planned as a separate package from the web app on purpose: it needs to be testable without a browser, and reusable later as an SDK or MCP server without dragging UI code along with it.

## Local setup

**There is nothing to run yet.** No package has a working entry point, and no `npm install` will produce a usable tool today. This section will be replaced with real setup instructions once `packages/core` has a working decode path — tracked in [docs/IMPLEMENTATION_STATUS.md](docs/IMPLEMENTATION_STATUS.md).

## Planned stack

| Layer | Choice | Why |
|---|---|---|
| Solana SDK | `@solana/web3.js` or `@solana/kit` | Final pick recorded in [docs/TECH_STACK.md](docs/TECH_STACK.md) once decoding work starts — not needed to make this decision before any decode code exists |
| Decoding | `@solana/spl-token` + native System Program layouts | Covers the two program types in v0.1 scope |
| AI | Claude or OpenAI API, constrained to decoded structured input | Explanation only — never given raw signing authority |
| Web app | Next.js, chat-style UI | Matches the "paste a transaction, get an explanation" interaction model, no wallet connect required |
| Auth | Email / social login | Deliberately not wallet-based — using LumenaSOL shouldn't require exposing a wallet |

Nothing here is locked in code yet; this table reflects current intent, not a dependency that's actually installed.

## Credentials

No API keys, private keys, seed phrases, or wallet credentials are stored in this repository, and none are needed to read or evaluate any of the current documentation.

## License

MIT
