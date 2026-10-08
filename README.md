# Crypto Portfolio Advisor

**Status:** In Development

Crypto Portfolio Advisor is an AI-assisted decision-support platform for spot crypto portfolio management and swing trading. It is intended to help a trader evaluate portfolio context, risk, market conditions, and an existing trading plan before deciding whether to act.

The project addresses a common problem in discretionary trading: individual signals are easy to view in isolation, while exposure, concentration, available cash, invalidation, and portfolio-level risk are harder to consider consistently. The goal is to make those constraints explicit and produce decisions that are explainable, reviewable, and safe by design.

## Product principles

- Treat the portfolio, rather than an isolated asset or signal, as the unit of decision-making.
- Put deterministic calculations and risk constraints ahead of AI-generated reasoning.
- Keep `NO_TRADE` as a valid first-class outcome.
- Fail safely when market or portfolio data is stale, incomplete, or invalid.
- Require an invalidation case and acceptable risk/reward for actionable trades.
- Evaluate strategy assumptions with historical evidence before making performance claims.
- Keep trade execution manual in V1.

The approved V1 scope and principles are documented in [Trading Requirements](docs/product/trading-requirements.md).

## Planned capabilities

The product direction includes:

- Portfolio-aware guidance for buying, adding, holding, reducing, selling, and managing limit-order plans.
- A trend-following swing strategy focused on BTC, ETH, and SOL, primarily using 4-hour and daily timeframes.
- Deterministic position sizing, risk/reward checks, concentration controls, drawdown protection, and basic correlated-exposure awareness.
- A persistent trading plan whose proposed actions can be reviewed and updated.
- Research, backtesting, and evaluation of strategy assumptions.
- Clear explanations that separate calculated facts, constraints, and AI reasoning.
- A web dashboard, an iOS application, and a Telegram client for alerts and advisor interaction; Android may follow later.

These capabilities are planned and are not currently implemented.

## Technology direction

The intended direction is a client-independent backend serving multiple clients, with clear boundaries between deterministic portfolio and risk calculations, strategy research, AI-assisted reasoning, and external market or on-chain data providers. Specific frameworks, infrastructure, deployment choices, and the final system architecture remain undecided.

See [Architecture](docs/architecture/README.md) for the boundaries approved so far and [Architecture Decision Records](docs/adr/README.md) for how consequential technical choices will be documented.

## Development philosophy

Financial and trading correctness take priority over delivery speed. Development should use strong typing, comprehensive automated tests, explicit trade-offs, secure defaults, useful observability, and maintainable designs without unnecessary complexity. AI may automate repetitive implementation only after the underlying pattern is understood and established.

This repository is also a serious learning project for Python backend and full-stack engineering, AI engineering, Web3 concepts, and high-quality iOS development. Learning goals do not override product safety or engineering quality.

## Development status

### Current

- Initial product scope and trading requirements are documented.
- Initial architectural boundaries and the ADR process are documented.
- The repository is licensed under the MIT License.

### In progress

- Product requirements are being refined.
- Architecture and technology choices are being evaluated.
- Research and validation plans are being defined.

### Planned

- Research and backtesting foundations.
- Deterministic portfolio, risk, and strategy capabilities.
- AI reasoning with deterministic pre- and post-validation.
- A client-independent backend and external data integrations.
- Web, iOS, and Telegram clients.
- Production readiness, including security, observability, and deployment planning.
- Optional Android support after higher-priority clients.

## Roadmap

1. Establish product definitions, safety constraints, and evaluation criteria.
2. Research strategy assumptions and build reproducible backtesting and evaluation.
3. Design and validate the core architecture through explicit ADRs.
4. Implement deterministic portfolio, strategy, and risk foundations.
5. Add a constrained AI reasoning layer and deterministic output validation.
6. Deliver client experiences incrementally, beginning with the highest-value workflows.
7. Harden, observe, and evaluate the system before treating it as production-ready.

Roadmap order may change as research exposes new risks or requirements.

## Disclaimer

Crypto Portfolio Advisor is decision-support software, not financial advice. It does not guarantee outcomes or profitability. Crypto assets are volatile and can result in substantial or total loss. Users remain responsible for evaluating information and making all trading decisions.
