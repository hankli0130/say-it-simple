# 我真實發過的進度回報

## 向 PM 回報

```
11/19 Progress Update

- Completed
  - Released broadcast-service 0.5.0 - updated ads message structure.

- In Progress
  - Improving the otp-service architecture.
```

```
7/16 Phase 4 Progress Update
- Completed
  - Implement requirements for the broadcast service
  	- Default route fallback
  	- Language from request param
  	- Message types & forms
  	- General messages TOML
  	- Hot reload after config edits
    
- Doing
  - Implement requirements for the broadcast service
    - Multiple apps, messages isolated
    - Country/Region/City via IP2Location
  - Plan tests and deployment for the broadcast service
```

```
7/9 Phase 4 Progress Update
- Completed
  - Plan and design requirements of the broadcast service
    - Researched and analyzed routing rules
    - Planned and designed message types and formats
    - Researched the feasibility of multilingual message editing

- Doing
  - Plan and design requirements of the broadcast service
    - Implementing a small-scale architecture for the broadcast service
```

```
7/1 Phase 3 Progress Update

- Completed advance functions, including:
    - The account deletion in the OTP Service
    - The Root-Rust library integration
    - Manual testing of the account deletion flow
    - The documentation updates

- Doing
    - Test RevenueCat via stripe (Hugh has completed the setup of connecting Stripe account from RevenueCat)
```

```
6/26 Phase 2 Progress Update

- Completed RevenueCat integration, including:
  - External setup (Google Play and RevenueCat dashboard)
  - Code implementation and testing for `otp-service`
  - Manual testing of the user subscription flow via RevenueCat API
  - Confirmed no updates are required for the `root-rust` library (the integration works as is without modifying `root-rust`)

- Blockers:
  - Stripe test-mode setup is currently pending assistance from Hugh, who is the account owner.
```

## 向投資人回報

```
Hi Eunice,

Hope you had a great weekend as well.

I've wrapped up all current service requirements and am now focusing on optimizing multi-repo management, setting up CI, and iterating on feedback from the team.

Here's a quick breakdown:

Completed:
  - Updated the broadcast service message format for Vaneet.
  - Added message IDs to the broadcast service message struct for Hugh.

In progress:
  - Multi-repo management setup.
  - CI integration for `root-rust` and `root-android`
```

```
Hi Eunice, 

The broadcast service has been don and deployed. I'm working on the `root-rust` library integration. I expect I will complete the integration today. 
```

```
Hi Eunice, 

Here is the latest update for the progress of Phase 2:

I am currently testing the user subscription flow for BangVPN, which involves integration with RevenueCat and the `otp-service`. Additionally, I'm currently in the progress of setting up Stripe.

Completed:
- External setup: Google Play configuration is completed, and I have successfully tested and verified the payment screen on the Android client.
- `OTP-Service`: Code review and bug fixing for Phase 2 has been completed.

Please let me know if you need any further details. 
```