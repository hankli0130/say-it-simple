---
audience: US Boss/teams/investors
channel: Mattermost
goal: 通知發布後端 OTP API service 新版本
---

Hi @all,

I just released `otp-service` v0.6.1. There are no required actions for client apps.

This update includes a fix for the cleanup job, persistent cleanup audit logs, and a new email driver for local development.

Please let me know if you have any questions. Thank you!

## Review

這版的段落順序很清楚。第一段交代版本和對用戶端的影響，第二段再列出更新內容。

- `There are no required actions for client apps.` 文法正確。如果要告訴負責 app 的同事「你們不用做任何事」，用 `Client app teams don’t need to take any action.` 更直接。
- `persistent cleanup audit logs` 有好幾個修飾語連在一起。前面已經提到 `the cleanup job`，寫成 `persistent audit logs for that job`，讀者更容易看出這些紀錄屬於哪個作業。

**可直接發布的版本**

> Hi @all,
>
> I just released `otp-service` v0.6.1. Client app teams don’t need to take any action.
>
> This update includes a fix for the cleanup job, persistent audit logs for that job, and a new email driver for local development.
>
> Please let me know if you have any questions. Thank you!

**口說練習**｜看著 `v0.6.1 → cleanup fix and logs → local email driver → no action` 試著說一遍。

> I just released version 0.6.1 of the OTP service. I fixed an issue with the cleanup job and added persistent audit logs for it. I also added an email driver for local development. Client app teams don’t need to do anything for this release.

**會議追問**  
*Do we need to update our client apps for this release?*  
*No, you don’t need to make any changes on your end.*
