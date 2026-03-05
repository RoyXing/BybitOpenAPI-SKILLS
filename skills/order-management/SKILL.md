# Skill: order-management

## Purpose
下单/改单/撤单/批量下单，含幂等与精度控制。

## Key REST Endpoints
- POST /v5/order/create
- POST /v5/order/amend
- POST /v5/order/cancel
- GET /v5/order/realtime
- GET /v5/order/history
- GET /v5/execution/list

## Best Practices
- 使用 `orderLinkId` 做幂等，防止重试重复下单。
- 下单前先取 instruments-info，按 `qtyStep` 和 `minOrderQty` 量化。
- 现货挂单会锁仓，卖出前需撤挂单。

## Error Handling
- retCode=170137：数量精度错误
- retCode=170131：最小下单额/数量不满足
- retCode=10001：参数缺失

## Example
```
POST /v5/order/create
{
  "category":"linear",
  "symbol":"BTCUSDT",
  "side":"Buy",
  "orderType":"Market",
  "qty":"0.001",
  "orderLinkId":"bot-001"
}
```
