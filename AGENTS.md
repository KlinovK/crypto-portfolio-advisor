# Agent Working Agreement

This file is the operational contract for coding agents working in this repository.

## Priority

Optimize in this order:

1. Correctness
2. Safety
3. Maintainability
4. Learning value
5. Delivery speed

Do not optimize for the amount of generated code or for development speed.

## Before changing files

- Inspect Git status and preserve unrelated user changes.
- Read the relevant requirements, accepted ADRs, and approved plans.
- Confirm the task scope and the applicable AI-assistance mode.
- Identify financial, security, persistence, concurrency, and AI-boundary risks.

## Scope discipline

- Implement only approved requirements. Do not expand scope or add speculative features without explicit approval.
- Prefer the simplest design that satisfies the approved behavior.
- Do not add abstractions for hypothetical future requirements.
- Do not perform unrelated refactoring.
- State assumptions when they are necessary; do not silently resolve an undecided product or architecture question.

## Conflicts

- Do not silently resolve a material conflict among repository instructions, approved requirements, accepted ADRs, approved plans, or explicit task instructions.
- Stop the affected work, explain the conflict, and request resolution before proceeding with the conflicting part. Do not treat a task instruction as an implicit override of an accepted decision, financial invariant, or repository safety rule.
- Non-material differences that do not affect implementation do not require escalation.

## Financial correctness and safety

- Financial calculations must be deterministic. AI or LLM output is never a financial source of truth and cannot bypass risk constraints.
- Do not use binary floating-point for financial domain values.
- Make financial precision and rounding rules explicit before implementing calculations. Do not invent exact rules that have not been approved.
- Treat invalid, stale, incomplete, or inconsistent critical data as a safe failure, not as permission to continue.
- Preserve the deterministic-before-AI and deterministic-after-AI validation boundary defined by the product requirements.

## Architecture

- Respect established dependency boundaries, accepted ADRs, and approved plans.
- Do not create a new architectural layer without a concrete requirement and explicit justification.
- Do not introduce microservices, event-driven infrastructure, repositories, Unit of Work, CQRS, event sourcing, or similar patterns merely for portfolio value.
- Record significant architectural reasoning. Propose an ADR when a decision is consequential or difficult to reverse.

## Code quality

- Use strong typing and make domain invariants explicit.
- Model errors intentionally and avoid hidden side effects.
- Avoid unnecessary dependencies.
- Prefer readable, maintainable code over clever code.
- Use comments to explain why; do not restate obvious code.
- Follow established project conventions. Do not invent language-specific style rules before they are approved.

## Testing

- Add appropriate automated tests for behavioral changes.
- Test externally meaningful behavior and important invariants without overfitting to implementation details.
- Add regression coverage for bug fixes when practical.
- Use deterministic tests for deterministic financial logic.
- Do not weaken, delete, skip, or rewrite tests merely to make an implementation pass.

## AI-assistance modes

- **LEARN:** When a concept is new or important to the project owner, minimize generated implementation. Explain the concept and alternatives, use small examples, and develop a reference implementation where useful.
- **ASSIST:** When the design is understood, implement bounded work under explicit requirements and constraints.
- **AUTOMATE:** When a pattern is understood and established, automate repetitive implementation while following that pattern.

Use `ASSIST` when a task does not specify a mode. `AUTOMATE` requires explicit project-owner authorization; never infer it from task size, repetition, familiarity, or previous work. Do not silently escalate from `LEARN` to `ASSIST` or `AUTOMATE`, or from `ASSIST` to `AUTOMATE`. If the current mode cannot support the requested scope appropriately, surface the constraint instead of escalating authority.

## Git and handoff

- Keep changes scoped and inspect the final diff.
- Do not commit or push unless explicitly requested.
- Report modified files, decisions or assumptions, and verification results.
- Run the relevant quality checks before handoff and disclose anything not verified.
