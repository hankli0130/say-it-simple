---
audience: US Boss/team
channel: Mattermost
goal: 通知完成後端 OTP API service 和函式庫 `root-rust` 更新
---

Hi @all I've completed the backend and library for Phase 1

- OTP Service
	- Request OTP email
	- Verify OTP email
	- Receive JWT
	- Get resource from resource service through the JWT
	- Resend OTP email
	- Logout

- root-rust
	- Integrate all the APIs from the OTP service.
	- Update the resource APIs to v5

Here is the [root-rust](https://github.com/teoncom/root-rust) , please check.

I've also tested the library through Android client and I noticed that the functions accessing Directory Server v5 are not working. I've asked @hugh_hall  to check since he is responsible for the server. @vaneet @allenhu You can start with the OTP APIs.

Here is the [root-android](https://github.com/teoncom/root-android), please check for Android client development.

Please let me know if you have any questions. Thank you 🙏 