# Architecture Decision Records

Architecture Decision Records (ADRs) capture consequential technical decisions together with their context and trade-offs. They provide a durable explanation of why a choice was made and make it possible to revisit that choice when assumptions change.

## Process

1. Create an ADR when a decision has meaningful architectural impact, a difficult-to-reverse consequence, or an important trade-off.
2. Number files sequentially and use a short descriptive name, for example `0001-example-decision.md`.
3. Begin with `Proposed` status while the decision is under discussion.
4. Record the context, considered options, decision, and consequences.
5. Change the status to `Accepted` only after approval.
6. Do not rewrite the history of an accepted ADR. Create a new ADR that marks the earlier record as `Superseded` when the decision changes.

This directory contains no decision records yet because no specific architecture has been approved.

## Template

```markdown
# ADR NNNN: Short decision title

- **Status:** Proposed
- **Date:** YYYY-MM-DD
- **Decision owners:** Names or roles

## Context

What problem requires a decision? Include relevant requirements, constraints, and assumptions.

## Options considered

Describe the viable options and their meaningful trade-offs.

## Decision

State the chosen option and why it best fits the current constraints.

## Consequences

Describe positive and negative consequences, risks, follow-up work, and conditions that could justify revisiting the decision.
```
