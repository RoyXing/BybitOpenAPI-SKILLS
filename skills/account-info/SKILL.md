# Skill: account-info

## Purpose
账户/费率/API 权限自检。

## Key REST Endpoints
- GET /v5/account/wallet-balance
- GET /v5/account/fee-rate
- GET /v5/account/account-info

## Notes
- 统一账户（UNIFIED）建议作为默认 accountType。

## Example
```
/v5/account/wallet-balance?accountType=UNIFIED
```
