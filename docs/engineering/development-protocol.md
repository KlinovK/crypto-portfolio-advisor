# Development Protocol

## Purpose

The project uses a proportional development lifecycle that protects correctness while supporting deliberate learning. The full sequence is a guide, not a requirement to create an artifact or ceremony for every small change.

```text
Requirement -> Learn -> Design -> Plan -> ADR when justified
            -> Reference implementation -> Tests
            -> Agent assistance or automation -> Review -> Quality Gate
            -> Commit -> Portfolio/documentation checkpoint when meaningful
```

## Lifecycle

1. **Requirement** — State the behavior, constraints, acceptance criteria, and relevant safety conditions. Resolve material product ambiguity before implementation.
2. **Learn** — Investigate concepts that are new or important to the project owner. Compare alternatives and validate assumptions without prematurely building the full solution.
3. **Design** — Define the smallest coherent solution within approved boundaries. Make domain invariants, data flow, failure behavior, and trade-offs explicit.
4. **Plan** — For a bounded change that benefits from sequencing, record the implementation steps and verification approach. Small, obvious changes may proceed without a written plan.
5. **ADR when justified** — Record why a consequential or difficult-to-reverse architectural choice was selected. Routine implementation decisions do not need an ADR.
6. **Reference implementation** — Establish a small, understandable example of an unfamiliar or reusable pattern before scaling it. Keep it production-quality when it will remain in the product.
7. **Tests** — Define and verify externally meaningful behavior, important invariants, failure cases, and regression coverage. Deterministic financial logic requires deterministic tests.
8. **Agent assistance or automation** — Use the task's `LEARN`, `ASSIST`, or `AUTOMATE` mode, defaulting to `ASSIST` when omitted. `AUTOMATE` requires explicit project-owner authorization and applies only after the pattern is understood and established.
9. **Review** — Inspect the implementation, tests, documentation, and actual diff for correctness, scope, maintainability, and risk. High-risk changes require explicit human review of the applicable risk-specific invariants and boundaries and the verification evidence that they remain preserved. Independent or adversarial review may be added when the risk justifies it.
10. **Quality Gate** — Apply the repository quality checklist and resolve known correctness issues. Record any checks that could not be run.
11. **Commit** — After review and only when authorized, create a focused commit whose message describes the completed change.
12. **Portfolio or documentation checkpoint** — When work demonstrates a meaningful capability or changes durable understanding, update public or internal documentation truthfully. Do not manufacture milestones for routine changes.

## Artifact responsibilities

These artifacts serve different purposes and should not substitute for one another:

- **Requirement:** what behavior is needed and which constraints it must satisfy.
- **Plan:** how a bounded change will be implemented and verified.
- **ADR:** why a significant architectural decision was selected over alternatives.
- **Prompt:** execution instructions and scope for a coding agent.

A prompt does not become durable project authority merely because work was discussed in chat. Important requirements and decisions belong in version-controlled repository artifacts. Not every change needs a written plan, and not every decision warrants an ADR.
