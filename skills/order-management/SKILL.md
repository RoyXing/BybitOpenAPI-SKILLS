# Skill: Order Management (Professional)

## Objective
Safe order lifecycle management: create / amend / cancel, with idempotency and precision enforcement.

## Preconditions
- Fetch instruments‑info and quantize by `qtyStep` + `tickSize`.
- Generate `orderLinkId` for idempotency.

## Core Endpoints
- POST `/v5/order/create`
- POST `/v5/order/amend`
- POST `/v5/order/cancel`
- GET `/v5/order/realtime`
- GET `/v5/order/history`
- GET `/v5/execution/list`

## Failure Taxonomy
- `170137`: qty precision invalid → re‑quantize
- `170131`: below min order size → increase qty
- `10001`: missing params → enforce symbol/category

## Example (Create)
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

## Example (Cancel)
```
POST /v5/order/cancel
{ "category":"spot", "symbol":"MNTUSDC", "orderId":"..." }
```
