# LumenaSOL

> AI-powered transaction intelligence for Solana.

Understand every transaction before you sign.

---

## Overview

LumenaSOL is an AI-powered transaction intelligence layer that helps users understand Solana transactions in plain English before approving them.

Instead of showing raw instructions, program IDs, and account addresses, LumenaSOL translates complex on-chain activity into clear, human-readable explanations. Users can instantly understand what a transaction does, which assets are involved, which programs are being called, and whether there are any notable risk indicators.

LumenaSOL does not replace wallets, execute transactions, or make decisions on behalf of users. Its goal is to improve transparency and confidence by making Solana transactions understandable to everyone.


---

## The Problem

Signing a transaction on Solana often requires trusting information that is difficult to interpret.

Most wallets display technical details such as:

Program IDs

Instruction indexes

Account addresses

Raw transaction metadata


While experienced developers may understand these details, most users cannot easily determine:

What exactly will happen after signing?

Which assets are leaving the wallet?

Which assets will be received?

Is this transaction performing actions beyond what I expect?

Is there anything unusual or potentially risky?


As Solana applications become increasingly sophisticated, transaction complexity grows while user understanding does not.

The result is simple:

Users are expected to approve transactions they do not fully understand.


---

## Our Solution

LumenaSOL bridges the gap between raw blockchain data and human understanding.

Instead of presenting technical transaction structures, LumenaSOL provides an intelligent explanation that summarizes:

What the transaction does

Assets sent

Assets received

Programs involved

Expected balance changes

Potential risk indicators

Plain-English explanation


The objective is not to decide for users.

The objective is to help users make informed decisions.


---

## Why AI?

AI is often used to automate actions.

LumenaSOL uses AI differently.

AI is responsible for translating complex blockchain activity into explanations that humans can easily understand.

Critical transaction analysis remains deterministic wherever possible.

AI never signs transactions.

AI never owns private keys.

AI never performs blockchain actions.

Instead, AI serves as an intelligent explanation layer on top of verified transaction data.


---

## Core Principles

LumenaSOL is built around several principles.

Human Understanding First

Blockchain data should be understandable without requiring technical expertise.


---

Deterministic Before Generative

Whenever objective blockchain data is available, deterministic analysis always comes first.

AI enhances explanations—it does not replace factual analysis.


---

Explain, Don't Decide

LumenaSOL provides context and explanations.

Final transaction approval always belongs to the user.


---

Non-Custodial

LumenaSOL never stores:

Private keys

Seed phrases

Wallet credentials


Users always sign transactions using their own wallet.


---

Read Before Trust

Every transaction deserves explanation before approval.


---

Product Vision

Our long-term vision is to become the intelligence layer for Solana transactions.

Today, wallets focus on executing transactions.

LumenaSOL focuses on helping users understand them.

As the ecosystem grows, transaction intelligence should become a standard layer available to every wallet, application, and AI agent interacting with Solana.


---

Planned Intelligence Modules

Transaction Intelligence

Explain transaction behavior before signing.

Features:

Transaction summary

Asset flow

Program identification

Balance changes

Human-readable explanation



---

Wallet Intelligence

Analyze wallet behavior.

Examples include:

Wallet activity

Portfolio overview

Transaction patterns

Behavioral insights



---

Token Intelligence

Provide contextual information about SPL tokens.

Examples:

Metadata

Token authority

Supply information

Holder distribution

Risk observations



---

Risk Intelligence

Highlight unusual transaction characteristics.

Examples:

Unknown programs

Large unexpected transfers

Authority changes

Suspicious transaction behavior


Risk indicators are informational and should not be interpreted as guarantees of safety.


---

Current Status

Area	Status

Product Vision	✅ Complete
Repository Foundation	✅ Complete
Documentation	🚧 In Progress
Architecture Design	🚧 In Progress
Transaction Parser	Planned
AI Explanation Engine	Planned
Wallet Integration	Planned
Web Application	Planned
Solana RPC Integration	Planned
Browser Extension	Future
SDK	Future


LumenaSOL is currently in the planning and architecture stage.

This repository documents the intended product and technical direction.

Production functionality has not yet been implemented.


---

High-Level Architecture

User

↓

Paste Transaction

↓

Transaction Parser

↓

Deterministic Analysis

↓

AI Explanation Layer

↓

Human-readable Intelligence

↓

User Reviews

↓

Wallet Approval

AI never bypasses wallet approval.

Every transaction remains under user control.


---

Repository Structure

LumenaSOL/

README.md

LICENSE

ROADMAP.md

CHANGELOG.md

CONTRIBUTING.md

docs/

PRODUCT.md

ARCHITECTURE.md

IMPLEMENTATION_STATUS.md

IMPLEMENTATION_PLAN.md

SECURITY_MODEL.md

AI_DESIGN.md

apps/

web/

packages/

core/

sdk/


---

Planned Technology Stack

Frontend

Next.js

React

TailwindCSS

TypeScript


Backend

Next.js API Routes

Node.js


Solana

@solana/web3.js

Solana RPC


AI

OpenAI

Claude

Structured prompting


Deployment

Vercel



---

Security Model

LumenaSOL is an intelligence platform.

It is not a wallet.

It is not a custody solution.

It never stores user credentials.

All transaction approvals remain inside supported wallet applications.

LumenaSOL only analyzes publicly available transaction information and provides explanations before users choose whether to continue.


---

Roadmap

Phase 1

Repository foundation

Documentation

Architecture


---

Phase 2

Transaction parser

Instruction decoding

Program detection


---

Phase 3

AI explanation engine

Risk intelligence

Wallet integration


---

Phase 4

Public MVP

Browser extension

SDK

Developer API


---

Open Source

LumenaSOL is being built as an open-source project.

Community contributions, feedback, and discussions are welcome as the project evolves.


---

License

Released under the MIT License.
