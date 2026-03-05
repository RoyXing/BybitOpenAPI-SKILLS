# Skill: WebSocket

## 目标
稳定的 WS 订阅与断线重连策略（公有/私有）。

## 公共频道
wss://stream.bybit.com/v5/public/{market}
- tickers.{symbol}
- orderbook.{depth}.{symbol}
- kline.{interval}.{symbol}

## 私有频道
wss://stream.bybit.com/v5/private
- auth（apiKey + expires + signature）
- subscribe: order / position / wallet

## 可靠性
- 断线重连后必须重订阅
- orderbook 需 REST snapshot + delta
- ping/pong 心跳保持连接
