# Quality Standards

These standards are technology-neutral. Specific languages, tools, thresholds, and automation will be selected only when justified by later implementation decisions.

## Standards

### Correctness and financial precision

- Behavior must satisfy approved requirements and preserve explicit domain invariants.
- Financial calculations must be deterministic, use representations suitable for the required precision, and must not use binary floating-point domain values.
- Precision, rounding, units, boundary conditions, and failure behavior must be explicit and tested once their domain rules are approved.
- No known unresolved correctness issue may pass a quality gate.

### Type safety and maintainability

- Use strong types to make invalid states harder to represent and important distinctions visible.
- Prefer cohesive, readable code with explicit dependencies and minimal hidden state.
- Add abstractions only when they clarify current requirements; avoid cleverness and speculative generalization.
- Keep changes focused and consistent with established conventions.

### Testing and reproducibility

- Test externally meaningful behavior, critical invariants, boundaries, and failure paths at a level appropriate to the change.
- Tests for deterministic logic must be deterministic and repeatable.
- Bug fixes should include regression coverage when practical.
- Results must be reproducible from documented inputs, assumptions, configuration, and commands where applicable.

### Error handling and fail-safe behavior

- Model expected failures intentionally and preserve useful diagnostic context.
- Do not silently ignore, coerce, or replace invalid critical input.
- Invalid, stale, incomplete, or inconsistent critical data must prevent unsafe recommendations or actions.
- Recovery and fallback behavior must not bypass financial or risk constraints.

### Security and observability

- Protect secrets and sensitive data, validate trust boundaries, and use least privilege where applicable.
- Treat external and AI-generated data as untrusted input until validated.
- Provide enough structured diagnostics to understand important decisions and failures without exposing secrets or sensitive information.
- Security-relevant and financially relevant events should be auditable at a level appropriate to the system design.

### Concurrency and persistence

- When concurrency is present, define ownership, ordering, atomicity, cancellation, and failure semantics explicitly.
- Prevent races, duplicate effects, partial state transitions, and stale writes where they could affect correctness.
- When persistence is present, preserve domain invariants across reads, writes, retries, and failures.

### Dependency discipline and documentation

- Add a dependency only when its current value outweighs its maintenance, security, and operational cost.
- Keep dependency direction consistent with approved architectural boundaries.
- Document public behavior, non-obvious constraints, operational requirements, and significant trade-offs close to their durable source of truth.
- Keep documentation consistent with the implementation and do not describe planned capability as complete.

## Quality Gate

Before a change is considered ready:

- [ ] Approved requirements and acceptance criteria are satisfied.
- [ ] The change remains within scope and introduces no speculative architecture or unrelated refactoring.
- [ ] Relevant domain invariants, financial precision rules, and fail-safe behavior are explicit and verified.
- [ ] Types, errors, dependencies, and side effects are intentional.
- [ ] Appropriate automated tests pass, including deterministic and regression tests where applicable.
- [ ] Test changes are justified and do not weaken required behavioral or invariant protection merely to make the implementation pass.
- [ ] Security, privacy, concurrency, persistence, and AI-boundary risks have been reviewed where applicable.
- [ ] Required diagnostics and documentation are accurate and do not expose sensitive data.
- [ ] Significant architectural or engineering decisions that require durable documentation are recorded in the appropriate repository artifact.
- [ ] Verification is reproducible, and any check not run is disclosed.
- [ ] The actual diff has been reviewed and contains no unrelated changes.
- [ ] There are no known unresolved correctness issues.
