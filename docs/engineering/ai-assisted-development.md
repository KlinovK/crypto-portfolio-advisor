# AI-Assisted Development

## Purpose

AI coding agents support implementation, analysis, and review; they do not replace product ownership or engineering judgment. Architecture and domain decisions remain human-reviewed, and agents work within repository instructions, authoritative requirements, accepted decisions, and the scope of the current task.

## Modes of assistance

### LEARN

Use `LEARN` when a concept is new or important to the project owner. The agent emphasizes explanation, alternatives, small examples, and an understandable reference implementation. Generated implementation is intentionally limited so that understanding develops before automation.

### ASSIST

Use `ASSIST` when the design and constraints are understood. The agent may implement scoped work, explain material choices, add tests, and perform self-review while keeping decisions visible to the owner.

### AUTOMATE

Use `AUTOMATE` when a pattern is already understood, reviewed, and established. The agent may generate repetitive work that follows that pattern, but must still satisfy the same tests, review, and quality standards as manually written code.

The mode is part of the task contract. If a task does not specify one, use `ASSIST`. `AUTOMATE` requires explicit project-owner authorization and must not be inferred from task size, repetition, familiarity, or previous work. An agent must not silently escalate from `LEARN` to `ASSIST` or `AUTOMATE`, or from `ASSIST` to `AUTOMATE`. If the current mode cannot support the requested scope appropriately, the agent surfaces that constraint instead of escalating authority.

## Professional use

- AI must not fabricate requirements, invent financial rules, or silently resolve undecided architecture.
- Repetitive code is automated only after its pattern is understood and established.
- Generated code receives the same correctness, safety, maintainability, testing, security, and documentation scrutiny as manually written code.
- Agent self-review is useful but is not sufficient for important changes.
- High-risk changes require explicit human review of the applicable risk-specific invariants and boundaries and the verification evidence that they remain preserved. These may include financial calculations and precision, risk constraints, concurrency and cancellation behavior, security boundaries, persistence consistency and failure behavior, and AI/deterministic boundaries.
- Independent or adversarial review may be added when the risk justifies it; a second-agent review is not universally required.
- Agents disclose assumptions, limitations, and verification that was not completed.

## Durable project knowledge

Repository artifacts preserve important knowledge: requirements define behavior, plans sequence bounded work, and ADRs explain significant architecture decisions. Prompts and chat history may provide working context, but they are not the sole record of durable requirements or decisions.

This approach improves engineering quality by making constraints reviewable and generated work accountable to the same standards as other work. It improves learning by reserving explanation and reference implementation for unfamiliar concepts, then increasing automation only after understanding is established. AI assistance accelerates suitable work; it does not guarantee quality.
