# Skill: Asset Management (Professional)

## Objective
Transfer, convert, and audit assets with explicit safeguards.

## Core Endpoints
- GET `/v5/asset/transfer/query-inter-transfer-list`
- POST `/v5/asset/transfer/inter-transfer`
- POST `/v5/asset/exchange/quote-apply`
- POST `/v5/asset/exchange/quote-execute`

## Operational Notes
- Dust convert has minimum threshold; tiny balances may return `system error`.
- Default account type: UNIFIED.

## Example
```
POST /v5/asset/transfer/inter-transfer
{ "fromAccountType":"UNIFIED", "toAccountType":"CONTRACT", "coin":"USDT", "amount":"10" }
```
