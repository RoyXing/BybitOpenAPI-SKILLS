# Skill: asset-management

## Purpose
资产划转、兑换、提现、历史查询。

## Key REST Endpoints
- GET /v5/asset/transfer/query-inter-transfer-list
- POST /v5/asset/transfer/inter-transfer
- POST /v5/asset/exchange/quote-apply
- POST /v5/asset/exchange/quote-execute

## Notes
- Dust convert 可能存在最小阈值；极小余额会返回 system error。
- 先确认账户类型（UNIFIED）。

## Example
```
POST /v5/asset/transfer/inter-transfer
{ "fromAccountType":"UNIFIED", "toAccountType":"CONTRACT", "coin":"USDT", "amount":"10" }
```
