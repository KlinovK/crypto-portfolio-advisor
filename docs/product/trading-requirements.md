# V1 Trading Requirements

## Purpose and status

This document records the approved trading requirements for the first product version. It defines product behavior and safety boundaries, not a completed implementation or a claim that the strategy is profitable.

## Trading model

V1 provides portfolio-level decision support for spot swing trading. It does not execute trades.

- **Markets:** spot only
- **Leverage:** none
- **Short selling:** not supported
- **Trading style:** swing trading
- **Primary timeframes:** 4H and 1D
- **Entry refinement:** 1H may be used when appropriate
- **Initial asset universe:** BTC, ETH, and SOL
- **Stablecoins:** USDT and USDC
- **Execution:** manual in V1

## Conceptual actions

The product may represent the following decisions or plan actions:

- `BUY`
- `ADD`
- `HOLD`
- `REDUCE`
- `SELL`
- `PLACE_LIMIT`
- `MODIFY_LIMIT`
- `CANCEL_LIMIT`
- `NO_TRADE`

These are conceptual recommendations for decision support. They do not imply automated order execution. `NO_TRADE` is a first-class valid decision, not a missing result or fallback error.

## Strategy direction

V1 will explore a trend-following swing strategy. Initial setups are:

- Trend continuation
- Pullback in trend
- Breakout and retest

Counter-trend and reversal trading are not primary V1 strategies. Exact entry, exit, invalidation, and setup qualification rules remain to be researched, tested, and approved.

## Portfolio principles

Every decision must be evaluated in portfolio context. The portfolio model must account for:

- A protected reserve that is not ordinary trading capital
- Trading cash available for planned activity
- Existing positions
- Total exposure and concentration
- Basic correlated crypto exposure
- A persistent Trading Plan

The Trading Plan records intended actions and their lifecycle rather than treating each recommendation as isolated. An existing plan action may transition to:

- `KEEP`
- `MODIFY`
- `CANCEL`
- `FILLED`
- `EXPIRED`

The precise plan schema and lifecycle rules remain an open design decision.

## Risk principles

Risk decisions must be deterministic, testable, and independent of AI discretion.

- A deterministic Risk Engine owns enforceable risk constraints.
- AI cannot override hard risk constraints.
- Position sizing is deterministic.
- Every actionable trade requires an explicit invalidation condition.
- Actionable trades must pass risk/reward validation.
- Position sizing must account for volatility.
- Decisions must check portfolio exposure and concentration.
- Decisions must include basic awareness of correlated crypto exposure.
- Drawdown protection must reduce or prevent risk-taking according to deterministic rules.
- Stale, incomplete, inconsistent, or invalid required data must fail safe.
- The risk model must distinguish hard constraints from soft constraints.

Hard and soft thresholds, risk budgets, drawdown rules, and fail-safe behavior will be specified and validated before implementation.

## AI principles

AI is not the financial source of truth. The processing direction is:

```text
deterministic calculations -> AI reasoning -> deterministic validation
```

- Deterministic calculations establish portfolio facts, market-derived values, and enforceable constraints before AI is invoked.
- AI may reason about context, rank eligible choices, compare scenarios, and explain a result.
- Deterministic validation checks AI output before it can be presented as an actionable recommendation.
- AI output must not bypass risk rules, fabricate missing inputs, or convert unsafe data into a recommendation.

## Research and evaluation

Strategy assumptions must be evaluated using historical data. Backtesting and evaluation are core product capabilities, not optional extras.

Research must make its data, assumptions, limitations, costs, and evaluation method inspectable. The project must not claim strategy profitability until appropriate evidence exists, and any future results must be presented with their limitations rather than as guarantees.

## Client direction

Planned clients are:

- A web dashboard
- An iOS application
- A Telegram bot for actionable signals, risk alerts, Trading Plan changes, and advisor interaction
- An optional Android client at a later stage

Telegram is a delivery and interaction client. Trading, portfolio, strategy, and risk logic must not live in the bot.

## Engineering principles

- Correctness over development speed
- Explicit trade-offs
- Strong typing
- Comprehensive automated testing
- Maintainability
- Security
- Observability
- Avoidance of unnecessary complexity and overengineering
- Important architectural decisions recorded as ADRs
- AI-assisted automation of repetitive implementation only after the underlying pattern is understood and established

These principles apply throughout research, implementation, and client development.
