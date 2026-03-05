# Example: End‑to‑End Execution (AI Agent)

## Goal
From signal to execution with safety checks.

## Step 0 — Precision Gate
```
GET /v5/market/instruments-info?category=linear&symbol=BTCUSDT
```
Extract: `minOrderQty`, `qtyStep`, `tickSize` and quantize all sizes.

## Step 1 — Market Context
```
GET /v5/market/tickers?category=linear&symbol=BTCUSDT
```

## Step 2 — Signal
Agent computes side + size using risk ≤ 1% equity.

## Step 3 — Idempotent Order
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

## Step 4 — Fill Verification
```
GET /v5/order/realtime?category=linear&symbol=BTCUSDT&orderId=...
```

## Step 5 — TP/SL
```
POST /v5/position/trading-stop
{ "category":"linear", "symbol":"BTCUSDT", "takeProfit":"30000", "stopLoss":"25000" }
```

## Step 6 — Live Monitoring (WS)
Subscribe: `order`, `position`, `wallet`

---
**Failure handling**: retry ≤ 2 on network errors only.
