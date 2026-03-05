# Skill: Asset Management

## 目标
资金划转、兑换、提现与历史查询。

## 关键接口
- GET `/v5/asset/transfer/query-inter-transfer-list`
- POST `/v5/asset/transfer/inter-transfer`
- POST `/v5/asset/exchange/quote-apply`
- POST `/v5/asset/exchange/quote-execute`

## 注意事项
- Dust convert 有最小阈值，过小余额可能 `system error`
- 默认使用 UNIFIED 账户

## 示例
```
POST /v5/asset/transfer/inter-transfer
{ "fromAccountType":"UNIFIED", "toAccountType":"CONTRACT", "coin":"USDT", "amount":"10" }
```
