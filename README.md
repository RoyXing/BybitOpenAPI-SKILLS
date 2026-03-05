# Bybit OpenAPI Skills (AI‑Agent Edition)

高可信、可执行的 Bybit V5 OpenAPI 技能卡集合，专为 AI agent 设计：强调**可操作步骤**、**参数精度**、**幂等性**与**风控边界**。

## 覆盖范围
- Market / Order / Position / Trade / Account / Asset / WebSocket

## 适用场景
- 让 AI agent 在真实交易环境下**安全、可控**地调用 Bybit OpenAPI
- 作为“可执行 playbook”，避免 agent 只读文档却无法落地

## 使用方式（给 AI agent）
1) 先读本 README，理解全局风控与命名规范
2) 根据任务选择对应 skill：
   - 行情 → `skills/market-data/`
   - 下单/撤单 → `skills/order-management/`
   - 仓位管理 → `skills/position-management/`
   - 交易流程编排 → `skills/trade-execution/`
   - 账户/权限 → `skills/account-info/`
   - 资金划转/兑换 → `skills/asset-management/`
   - WS 实时订阅 → `skills/websocket/`
3) 严格执行 skill 中的**前置检查**与**错误处理**

## 统一风控与工程原则（必须遵守）
- **精度优先**：下单前必须读取 `instruments-info` 并按 `qtyStep / minOrderQty / tickSize` 量化
- **幂等性**：下单必须使用 `orderLinkId` 防止重复下单
- **风险上限**：默认单笔风险 ≤ 1% 账户权益；杠杆默认 ≤ 5x
- **失败重试**：最多 2 次，且必须区分网络异常与参数错误
- **WS 可靠性**：断线重连后必须重新订阅；orderbook 需 REST snapshot 再接 delta

## 目录结构
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

## 版本说明
- Bybit V5 OpenAPI
- 适配 Unified 账户

---
**提示**：如果你是人类操作者，建议先从 `trade-execution` 的完整流程模板开始。
