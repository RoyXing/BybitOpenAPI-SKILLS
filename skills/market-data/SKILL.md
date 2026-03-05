# Skill: Market Data (Professional)

## Objective
Provide deterministic market data retrieval for AI agents (REST + WS), with precision‑aware constraints and reliability rules.

## Preconditions
- Resolve `category` (spot/linear/inverse/option)
- Fetch `instruments-info` to obtain:
  - `minOrderQty`, `qtyStep`, `tickSize`, `basePrecision`

## Core REST Endpoints
- GET `/v5/market/time`
- GET `/v5/market/tickers`
- GET `/v5/market/instruments-info`
- GET `/v5/market/orderbook`
- GET `/v5/market/kline`

## WS Topics (Public)
- `tickers.{symbol}`
- `orderbook.{depth}.{symbol}`
- `kline.{interval}.{symbol}`
- `publicTrade.{symbol}`

## Reliability Requirements
- **Orderbook**: On reconnect, always re‑pull REST snapshot, then apply deltas.
- **Rate limits**: Exponential backoff on 429/413.

## Output Contract
- price, 24h change, volume
- source = REST or WS

## Example
```
/v5/market/tickers?category=linear&symbol=BTCUSDT
```
