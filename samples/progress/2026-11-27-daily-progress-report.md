---
audience: US Boss/teams
channel: Mattermost
goal: 每日進度回報 - 完成重構 otp-service
---

- I finished refactoring `otp-service`.
  - Configured Postgres to accept only local connections.
  - Made email address comparisons case-insensitive.
  - Added cleanup for expired OTPs, refresh tokens, and sessions.
  - Increased the maximum length of `sessions.client_id` to 255 characters.

## 口說練習

提示關鍵字：local connections → email matching → cleanup → client ID length

> I finished refactoring the OTP service. Postgres now accepts only local connections, and the service ignores capitalization when it compares email addresses. I also added cleanup for three kinds of expired data: OTPs, refresh tokens, and sessions. Finally, I raised the length limit for client IDs in the sessions table to 255 characters.

## 會議追問

*What happens if someone types their email address in all caps?*

*The service treats it as a match as long as the only difference is capitalization.*
