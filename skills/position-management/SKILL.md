# Skill: Position Management (Professional)

## Objective
Control leverage, TP/SL, and position integrity with explicit parameter validation.

## Core Endpoints
- GET `/v5/position/list` (**requires** symbol or settleCoin)
- POST `/v5/position/set-leverage`
- POST `/v5/position/trading-stop`

## Operational Notes
- UTA: confirm `positionIdx` and `tradeMode`.
- Always re‑query `/position/list` after changes.

## Example
```
POST /v5/position/set-leverage
{ "category":"linear", "symbol":"BTCUSDT", "buyLeverage":"3", "sellLeverage":"3" }
```
