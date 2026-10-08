# Architecture

## Status

The system architecture is under design. No final architecture, framework, deployment model, data store, provider, or infrastructure choice has been approved yet. Those decisions will be made only as product and research requirements become sufficiently clear, with consequential choices recorded as Architecture Decision Records.

## Approved boundaries

Current planning recognizes only the following high-level boundaries:

- **Deterministic portfolio and risk calculations:** owns calculated portfolio state, position sizing, and enforceable risk constraints.
- **Strategy and research subsystem:** supports strategy definition, historical evaluation, backtesting, and evidence gathering.
- **AI reasoning layer:** reasons about, ranks, contextualizes, and explains eligible decisions; it is bounded by deterministic inputs and validation.
- **Client-independent backend:** exposes product capabilities without placing core trading logic in a particular client.
- **Multiple clients:** planned consumers include web, iOS, and Telegram, with Android optional and later.
- **External market and on-chain data providers:** supply inputs whose freshness, completeness, provenance, and failure behavior must be handled explicitly.

The required decision flow is:

```text
deterministic calculations -> AI reasoning -> deterministic validation
```

This boundary prevents AI from becoming the financial source of truth or overriding risk constraints.

## Intentionally undecided

The following remain open and must not be inferred from this document:

- Frameworks and programming libraries
- Service and module decomposition
- APIs and communication protocols
- Data storage and caching
- Hosting, deployment, and delivery infrastructure
- Market and on-chain data providers
- AI models, providers, prompts, and orchestration
- Client implementation details
- Security and observability tooling

These choices should follow validated requirements and explicit trade-off analysis, not precede them.
