# Skill: Trade Execution (Professional)

## Objective
Orchestrate the full trading chain: validate → decide → execute → verify → manage.

## Canonical Flow
1) **Precision gate**: GET instruments‑info
2) **Market context**: tickers / kline
3) **Signal**: strategy outputs side + size
4) **Idempotent order**: orderLinkId
5) **Fill verification**: order/execution
6) **Risk control**: TP/SL via trading‑stop
7) **Live monitoring**: WS order/position

## Default Risk Policy
- risk/position ≤ 1% equity
- leverage ≤ 5x
- retry ≤ 2, only on network errors

## Output Contract
- execution summary (side/qty/price)
- realized & unrealized PnL snapshot
