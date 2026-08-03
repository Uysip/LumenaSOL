# 07 — Agentic Workflow

## Status

This document describes how AI-assisted engineering is being used for planning and how it is intended to be used during implementation. It does not claim that production coding work has already been completed.

## Tools

### solana.new

solana.new is intended to support project ideation, Solana-specific planning, and grant-oriented structure. For LumenaSOL, it helps frame the project as a Solana-native transaction intelligence layer rather than a generic scanner.

Expected uses during implementation:

- Clarify Solana architecture choices.
- Compare implementation approaches for transaction decoding.
- Keep MVP scope aligned with Solana-specific user needs.
- Assist with milestone planning and review preparation.

### Codex

Codex is being used as an engineering copilot for repository work, documentation generation, implementation planning, and future code iteration.

Expected uses during implementation:

- Draft and refine decoder schemas.
- Implement deterministic parsing and decoding code with human review.
- Generate fixture tests and edge-case checklists.
- Review code for consistency with the security model.
- Keep documentation synchronized with actual implementation status.

## Intended AI-Assisted Development Loop

1. Define or refine a small implementation task.
2. Ask the agent to inspect current repository state before coding.
3. Implement the smallest useful change.
4. Run tests or checks where available.
5. Review outputs against deterministic-first and non-custodial constraints.
6. Update implementation status honestly.
7. Commit changes with clear messages.

## Human Review Responsibilities

AI assistance does not remove the need for human engineering judgment. The project owner remains responsible for:

- Confirming product scope.
- Reviewing decoder correctness.
- Verifying security claims.
- Ensuring documentation matches implementation.
- Deciding whether the MVP is ready for grant submission.

## Guardrails for Agentic Work

- Do not claim unimplemented capabilities.
- Do not add wallet custody or signing behavior.
- Do not expand scope into token safety scoring or wallet reputation analysis.
- Do not let AI explanations override deterministic facts.
- Prefer explicit unsupported states over guessed behavior.
- Keep project status updated as implementation progresses.

## Current Session Usage

During this planning session, Codex was used to generate a structured grant artifact package from the user's stated requirements and existing repository README. No coding implementation, benchmark, screenshot, deployed demo, or test result is claimed as completed.
