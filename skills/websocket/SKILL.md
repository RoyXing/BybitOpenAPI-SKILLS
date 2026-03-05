# Skill: websocket

## Purpose
公共/私有 WS 连接、认证、断线重连、消息一致性处理。

## Public WS
wss://stream.bybit.com/v5/public/{market}
- tickers.{symbol}
- orderbook.{depth}.{symbol}
- kline.{interval}.{symbol}

## Private WS
wss://stream.bybit.com/v5/private
- auth (apiKey + expires + signature)
- subscribe: order / position / wallet

## Reliability
- 断线重连：重连后必须重订阅
- orderbook：重连后先拉 REST snapshot，再接 delta
- 心跳：按服务端 ping/pong

## Error Handling
- 频率限制：降低订阅数量/频率
- 认证失败：检查 timestamp 与签名
