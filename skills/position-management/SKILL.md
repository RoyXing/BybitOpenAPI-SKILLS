# Skill: Position Management

## 目标
查询与管理仓位（杠杆、止盈止损、仓位模式）。

## 关键接口
- GET `/v5/position/list`（必须提供 symbol 或 settleCoin）
- POST `/v5/position/set-leverage`
- POST `/v5/position/trading-stop`

## 注意事项
- UTA 下 positionIdx 需要匹配仓位方向
- 下单后立即查询 `position/list` 确认生效

## 示例
```
POST /v5/position/set-leverage
{ "category":"linear", "symbol":"BTCUSDT", "buyLeverage":"3", "sellLeverage":"3" }
```
