# Skill: Order Management

## 目标
安全下单/撤单/改单（含幂等与精度校验），适配自动化交易场景。

## 前置条件
- 拉 `instruments-info`，按 `qtyStep / minOrderQty / tickSize` 量化
- 使用 `orderLinkId` 作为幂等 ID

## 关键接口
- POST `/v5/order/create`
- POST `/v5/order/amend`
- POST `/v5/order/cancel`
- GET `/v5/order/realtime`
- GET `/v5/order/history`
- GET `/v5/execution/list`

## 错误处理
- `170137` 数量精度错误 → 按 `qtyStep` 修正
- `170131` 最小下单额不足 → 增加 qty
- `10001` 参数缺失 → 补齐 symbol/category

## 示例（下单）
```
POST /v5/order/create
{
  "category": "linear",
  "symbol": "BTCUSDT",
  "side": "Buy",
  "orderType": "Market",
  "qty": "0.001",
  "orderLinkId": "bot-001"
}
```

## 示例（撤单）
```
POST /v5/order/cancel
{ "category":"spot", "symbol":"MNTUSDC", "orderId":"..." }
```
