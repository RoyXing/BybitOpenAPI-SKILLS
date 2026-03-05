# Skill: WebSocket (Professional)

## Objective
Stable WS subscription with reconnection and consistency guarantees.

## Public WS
wss://stream.bybit.com/v5/public/{market}
- tickers.{symbol}
- orderbook.{depth}.{symbol}
- kline.{interval}.{symbol}

## Private WS
wss://stream.bybit.com/v5/private
- auth (apiKey + expires + signature)
- subscribe: order / position / wallet

## Reliability Guarantees
- Reconnect ⇒ re‑subscribe
- Orderbook ⇒ REST snapshot before delta
- Heartbeat ⇒ follow server ping/pong

## Failure Handling
- auth failed ⇒ re‑sign with fresh timestamp
- rate limited ⇒ reduce subscription rate
