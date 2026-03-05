# Skill: market-data

## Purpose
行情与市场数据获取（REST + WS），含 kline、ticker、orderbook。

## Key REST Endpoints
- GET /v5/market/time
- GET /v5/market/tickers (category)
- GET /v5/market/instruments-info (category)
- GET /v5/market/orderbook (category, symbol, limit)
- GET /v5/market/kline (category, symbol, interval, start, end)

## WS Topics (public)
- tickers.{symbol}
- orderbook.{depth}.{symbol}
- kline.{interval}.{symbol}
- publicTrade.{symbol}

## Precision / Limits
- 使用 instruments-info 的 lotSizeFilter / priceFilter 获取：
  - basePrecision, minOrderQty, qtyStep, tickSize
- orderbook 订阅先 snapshot 再 delta；断线重连需重新拉 snapshot。

## Error Handling
- 429/413：降频重试
- 10001: 参数缺失/错误

## Example (REST)
```
/v5/market/tickers?category=linear&symbol=BTCUSDT
```
