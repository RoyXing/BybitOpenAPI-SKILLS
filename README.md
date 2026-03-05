# Bybit OpenAPI Skills — AI Agent Playbook (Professional Edition)

面向 AI agent 的高可信交易能力手册。强调**可执行、可验证、可回滚**。

## Why this exists
- 将 Bybit V5 OpenAPI 从“参考文档”提升为**工程级操作手册**
- 降低 agent 的幻觉与试错成本（精度、幂等、风控一体化）

## Scope
- Market / Order / Position / Trade / Account / Asset / WebSocket
- **Full V5 Reference**: `skills/bybit-v5/SKILL.md` (complete endpoint list)

## Operating Principles（硬规则）
1) **精度先行**：先拉 instruments-info，再下单
2) **幂等保障**：所有下单必须带 orderLinkId
3) **风控优先**：单笔风险 ≤ 1%，杠杆 ≤ 5x（默认）
4) **失败可恢复**：最多 2 次重试，区分网络错误与参数错误
5) **WS 可靠性**：断线重连后必须重新订阅；orderbook 需 REST snapshot + delta

## How to Use
- 先读本 README
- 按任务选择 skill：
  - 行情 → `skills/market-data/`
  - 下单/撤单 → `skills/order-management/`
  - 仓位管理 → `skills/position-management/`
  - 交易流程 → `skills/trade-execution/`
  - 账户/权限 → `skills/account-info/`
  - 资金划转/兑换 → `skills/asset-management/`
  - WS 实时订阅 → `skills/websocket/`

## End‑to‑End Example
- See `skills/trade-execution/EXAMPLE.md`

## Directory Layout
```
skills/
  market-data/
  order-management/
  position-management/
  trade-execution/
  account-info/
  asset-management/
  websocket/
```

## Versioning
- Bybit V5 OpenAPI
- Unified Account (UTA)

---
**定位**：这不是教程，而是“可执行的工程规范”。
