# Skill: trade-execution

## Purpose
完整交易执行流程（查 → 算 → 下 → 监 → 管）。

## Workflow
1) 拉 instruments-info 获取精度/最小下单额
2) 拉 tickers / kline 计算信号
3) 生成 orderLinkId 幂等下单
4) 下单后查询 order/execution 确认成交
5) 设置 TP/SL 或追踪止损
6) WS 订阅订单/仓位变化

## Risk Guardrails
- 单笔风险 <= 1% 账户权益
- 最大杠杆 <= 5x（默认）
- 失败重试次数 <= 2

## Example
结合 order-management + position-management。
