# Skill: position-management

## Purpose
仓位查询、杠杆设置、止盈止损设置、模式切换。

## Key REST Endpoints
- GET /v5/position/list
- POST /v5/position/set-leverage
- POST /v5/position/trading-stop

## Notes
- /v5/position/list 必须提供 symbol 或 settleCoin。
- 设置 TP/SL 前确认 positionIdx 与 tradeMode。

## Example
```
POST /v5/position/set-leverage
{ "category":"linear", "symbol":"BTCUSDT", "buyLeverage":"3", "sellLeverage":"3" }
```
