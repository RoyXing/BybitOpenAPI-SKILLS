# Skill: Market Data

## 目标
为 AI agent 提供稳定的市场数据获取方法（REST + WebSocket），确保参数完整、精度可控、结果可验证。

## 前置条件
- 确认 `category`（spot/linear/inverse/option）
- 先拉 `instruments-info` 获取精度、最小下单量、tickSize

## 关键接口（REST）
- GET `/v5/market/time`
- GET `/v5/market/tickers`
- GET `/v5/market/instruments-info`
- GET `/v5/market/orderbook`
- GET `/v5/market/kline`

## 关键接口（WS 公共频道）
- `tickers.{symbol}`
- `orderbook.{depth}.{symbol}`
- `kline.{interval}.{symbol}`
- `publicTrade.{symbol}`

## 可靠性要求
- **orderbook**：断线重连后必须重新拉 REST snapshot，再接 delta
- **限频处理**：遇到 429，指数退避重试

## 输出格式建议（给 agent）
- 输出最新价格、24h 变化、成交量
- 标注数据来源（REST/WS）

## 示例（REST）
```
/v5/market/tickers?category=linear&symbol=BTCUSDT
```
