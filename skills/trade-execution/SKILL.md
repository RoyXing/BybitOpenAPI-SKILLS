# Skill: Trade Execution

## 目标
完整交易链路编排（查→算→下→监→管），面向 AI agent 的执行模板。

## 推荐流程
1) **校验精度**：GET instruments-info
2) **获取行情**：tickers / kline
3) **生成信号**：策略逻辑输出方向与仓位
4) **幂等下单**：orderLinkId
5) **确认成交**：order/execution
6) **设置 TP/SL**：position/trading-stop
7) **监控**：WS 订阅 order/position

## 风控默认值
- 单笔风险 ≤ 1% 账户权益
- 杠杆 ≤ 5x
- 失败重试 ≤ 2 次

## 输出
- 执行摘要（方向/数量/成本/风险）
- 实际成交与结果
